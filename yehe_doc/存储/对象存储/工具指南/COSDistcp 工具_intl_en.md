## Overview

COSDistCp is a MapReduce-based distributed copy tool for data copy between HDFS and COS. It allows users to filter/compress/aggregate files, limit read bandwidth, and preserve file attributes. Besides, based on the COS features, COSDistCp supports real-time data verification and incremental copy based on the length and CRC checksum.

## Operating Environment

#### Operating system

Linux

#### Software requirements

Hadoop 2.6.0 or above; Hadoop-COS 5.8.7 or above.

## Download and Installation

#### Obtaining the COSDistCp JAR package

Download link: [cos-distcp-1.2.jar](https://cos-sdk-archive-1253960454.file.myqcloud.com/cos-distcp/cos-distcp-1.2.jar)
>?You can verify whether the downloaded JAR package is complete according to the [MD5 checksum](https://cos-sdk-archive-1253960454.file.myqcloud.com/cos-distcp/cos-distcp-1.2-md5.txt) of the package.

#### Notes

In the Hadoop environment, install [Hadoop-COS](https://intl.cloud.tencent.com/document/product/436/6884?!preview=&!editLang=zh&from_cn_redirect=1&lang=en&pg=#download-and-installation) and then run the COSDistCp tool.


## How It Works

COSDistCp uses the MapReduce framework. Mappers group files, while multi-thread reducers perform file copy, compression, verification, and attribute preservation. If data copy or verification fails, the job may fail to be executed. If new files are added to your source file system or the file content changes, you can use the `--skipMode` or `--diffMode` parameter to compare the length or CRC checksum of the files to implement incremental copy.


## Parameters

You can run the `hadoop jar cos-distcp-${version}.jar --help` (`${version}` is the version number) command to view the COSDistCp-supported parameters. The following table describes the COSDistCp parameters:


| Attribute Key | Description | Default Value | Required |
| :------------------------------: | :----------------------------------------------------------- | :----: | :----: |
|  --help | Outputs parameters supported by COSDistCp. <br>Example: --help | None | No |
| --src=LOCATION | Location of the data to copy. This can be either an HDFS or COS location. <br>Example: --src=hdfs://user/logs/ | None | Yes |
|         --dest=LOCATION          | Destination for the data. This can be either an HDFS or COS location. <br>Example: --dest=cosn://examplebucket-1250000000/user/logs |   None  | Yes |
|       --srcPattern=PATTERN       | A regular expression that filters files in the source location. <br>Example: `--srcPattern='.*.log'`<br>**Note: Enclose your parameter in single quotation marks (') in case asterisks (*) are parsed by the shell.** | None | No |
|       --reducerNumber=VALUE       | The number of reducer processes. <br>Example: --reducerNumber=10 | 10 |   No   |
|       --workerNumber=VALUE       | The number of copying threads of each reducer. COSDistCp will create a copying thread pool for each reducer based on the set value. <br>Example: workerNumber=4 | 4 | No |
|      --filesPerMapper=VALUE      | The number of files input to each mapper. <br>Example: --filesPerMapper=10000 |  500000   |  No  |
|         --groupBy=PATTERN   | A regular expression to concatenate files that match the expression. <br>Example: --groupBy='.\*group-input/(\d+)-(\d+).*'   |  None  |   No   |
| --targetSize=VALUE | The size (in MB) of the files to create. This parameter is used together with `--groupBy`. <br>Example: --targetSize=10  | None |  No  |
|       --outputCodec=VALUE        | Specifies the compression codec to use for the copied files. This can take the values: `gzip`, `lzo`, `snappy`, `none`, or `keep`. Where, <br>1. `keep` indicates retaining the compression codec of the source files. <br>2. `none` indicates compression based on the extension. <br>Example: --outputCodec=gzip | keep | No |
|        --deleteOnSuccess         | If the copy operation is successful, this parameter specifies whether to delete the copied files from the source location immediately. <br>Example: --deleteOnSuccess | false | No |
| --multipartUploadChunkSize=VALUE | The size (in MB) of the multipart upload part transferred to COS using the Hadoop-COS plugin. COS supports up to 10,000 parts. You can set the value based on the file size.<br>Example: --multipartUploadChunkSize=20 | 8 |   No   |
|    --cosServerSideEncryption     | Specifies whether to use SSE-COS for encryption on the COS server side. <br />Example: --cosServerSideEncryption | false | No |
|      --outputManifest=VALUE      | Creates a file (Gzip compressed) that contains a list of all files copied to the destination location. <br>Example: --outputManifest=manifest.gz | None | No |
|    --requirePreviousManifest     | If set to `true`, `--previousManifest=VALUE` must be specified for incremental copy. <br>Example: --requirePreviousManifest |  false  | No |
|     --previousManifest=LOCATION     | A manifest file that was created during the previous copy operation. <br>Example: --previousManifest=cosn://examplebucket-1250000000/big-data/manifest.gz |  None  |   No   |
|        --copyFromManifest        | Copies files specified in `--previousManifest` to the destination file system. This is used together with `previousManifest=LOCATION`. <br>Example: --copyFromManifest |  false  |  No |
| --storageClass=VALUE | The storage class to use. Valid values are `STANDARD`, `STANDARD_IA`, `ARCHIVE`, `DEEP_ARCHIVE`, and `INTELLIGENT_TIERING`. For more information, please see [Storage Class Overview](https://intl.cloud.tencent.com/document/product/436/30925).  | None   |   No   |
|        --srcPrefixesFile=LOCATION        | A local file that contains a list of source directories, one directory per line. <br/>Example: --srcPrefixesFile=file:///data/migrate-folders.txt |  None    |   No  |
| --skipMode=MODE  | Verifies whether the source and destination files are the same before the copy. If they are the same, the file will be skipped. Valid values are `none` (no verification), `length`, `checksum`, and `length-checksum` (length + CRC checksum). <br/>Example: --skipMode=length | None | No |
| --checkMode=MODE | Verifies whether the source and destination files are the same when the copy is completed. If they are different, the copy will be stopped. Valid values are `none` (no verification), `length`, `checksum`, and `length-checksum` (length + CRC checksum).<br/>Example: --checkMode=length-checksum |  None  | No |
|   --diffMode=MODE    | Specifies the rule for obtaining the list of different files. Valid values are `length`, `checksum`, and `length-checksum` (`length` + CRC checksum). <br/>Example: --diffMode=length-checksum | None   | No  |
|  --diffOutput=LOCATION  | Specifies the output directory for the list of different files. This directory must be empty.<br/>Example: --diffOutput=/diff-output  |  None |  No  |
| --cosChecksumType=TYPE     | Specifies the CRC algorithm used by the Hadoop-COS plugin. Valid values are `CRC32C` and `CRC64`. <br/>Example: --cosChecksumType=CRC32C | CRC32C | No |
| --preserveStatus=VALUE | Specifies whether to copy the `user`, `group`, `permission`, `xattr`, and `timestamps` metadata of the source file to the destination file. Valid values are ugpxt (initials of `user`, `group`, `permission`, `xattr`, and `timestamps`, respectively). <br/>Example: --preserveStatus=ugpt | None | No |


## Examples

### Viewing the help option

Run the following command with `--help` to view the parameters supported by COSDistCp:

```plaintext
hadoop jar cos-distcp-${version}.jar --help
```
In the command above, `${version}` is the version ID of the COSDistCp. For example, the name of the COSDistCp JAR package (version 1.0) is `cos-distcp-1.0.jar`.

### Specifying the source and destination locations for the files to copy

Run the following command with the `--src` and `--dest` parameters:

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse
```

### Filtering source files with a regular expression

Run the following command with the `--srcPattern` parameter. In this example, only files whose extension is ".log" in the `/data/warehouse/logs` directory are copied.

```plaintext
hadoop jar cos-distcp-${version}.jar  --src /data/warehouse/logs --dest cosn://examplebucket-1250000000/data/warehouse --srcPattern='.*/logs/.*\.log'
```

### Specifying the number of reducers and the number of threads for each reducer process

Run the following command with the `--reducerNumber` and `--workersNumber` parameters. COSDistCp adopts a multi-process, multi-thread framework for the copy operation. You can:
- Use `--reducerNumber` to specify the number of reducer processes.
- Use `--workerNumber` to specify the number of threads for each reducer process.

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse/ --dest cosn://examplebucket-1250000000/data/warehouse --reducerNumber=10 --workerNumber=5
```

### Deleting the source files

Run the command with the `--deleteOnSuccess` parameter. The following example deletes the corresponding source files in the `/data/warehouse` directory immediately after they are copied from HDFS to COS:

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse --deleteOnSuccess
```

>!If `--deleteOnSuccess` is specified, each source file is deleted immediately after the file is copied, but not after all source files are copied.

### Restricting the read bandwidth for a single file

Run the command with the `--bandWidth` parameter (in MB). The following command example restricts the read bandwidth of each copied file to 10 MB/s:

```plaintext
hadoop jar cos-distcp-${version}.jar  --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse --bandWidth=10
```

### Specifying the checksum type of Hadoop-COS

Run the following command with the `--cosChecksumType` parameter. Valid values are `CRC32C` (default) and `CRC64`.

```plaintext
hadoop jar cos-distcp-${version}.jar  --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse --cosChecksumType=CRC32C
```

### Skipping files with the same length

Run the following command with the `--skipMode` parameter. The following command example skips files with the same length:
```plaintext
hadoop jar cos-distcp-${version}.jar  --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse  --skipMode=length
```

`--skipMode` is used to verify whether the source and destination files are the same before the copy. If they are the same, the file will be skipped. Valid values are `none` (no verification), `length`, `checksum`, and `length-checksum` (length + CRC checksum).

If the checksum algorithms of the source and destination file systems are different, the source file will be read for calculating a new checksum. If your source is HDFS, you can identify whether the HDFS source supports the COMPOSITE-CRC32C algorithm as follows:

```plaintext
hadoop fs  -Ddfs.checksum.combine.mode=COMPOSITE_CRC -checksum /data/test.txt
/data/test.txt  COMPOSITE-CRC32C        6a732798
```

### Verifying whether the source and destination files have the same CRC checksum

Run the following command with the `--checkMode` parameter. The following command example verifies whether the checksums of the source and destination files are the same when the copy is completed:

When you are copying files from a non-COS file system to COS, if the CRC algorithms of the source and Hadoop-COS are different, the CRC checksum will be calculated during the copy operation. When the copy operation is completed, the CRC checksum of the destination file will be obtained and compared with the calculated CRC checksum of the source file.

```plaintext
hadoop jar cos-distcp-${version}.jar   --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse --checkMode=checksum
```

### Specifying the output compression codec

Run the command with the `--outputCodec` parameter, which allows you to compress HDFS data to COS in real time to reduce storage costs. Valid values are `keep`, `none`, `gzip`, `lzop`, and `snappy`. If set to `none`, the files will be copied uncompressed. If set to `keep`, the files will be copied with no change in their compression. The following is an example:

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse/logs --dest cosn://examplebucket-1250000000/data/warehouse/logs-gzip --outputCodec=gzip
```

>!If not set to `keep`, the files will be decompressed and converted to the target compression format. Due to the difference in compression parameters, the content of the destination files might be different from that of the source files, but the files will be the same after decompression.

### Copying multiple directories

You can create a local file (for example, srcPrefixes.txt) and add multiple directories to copy to the file. After this, you can run the `cat` command to view the directories as follows:

```plaintext
cat srcPrefixes.txt 
/data/warehouse/20181121/
/data/warehouse/20181122/
```

Then, you can use `--srcPrefixesFile` to specify this file. The command is as follows:

```plaintext
hadoop jar  cos-distcp-${version}.jar --src /data/warehouse  --srcPrefixesFile file:///usr/local/service/hadoop/srcPrefixes.txt --dest  cosn://examplebucket-1250000000/data/warehouse/ --reducerNumber=20
```

### Generating the target manifest and specifying the previous manifest

Run the command with the `--outputManifest` and `--previousManifest` parameters.

- `--outputManifest` generates a local `manifest.gz` (Gzip compressed) file. When the copy operation is successful, the file is moved to the directory specified in `--dest`.
- `--previousManifest` specifies the destination files that are copied during the previous copy operation (`--outputManifest`). COSDistCp will skip files of the same size.

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse --dest  cosn://examplebucket-1250000000/data/warehouse/ --outputManifest=manifest.gz --previousManifest= cosn://examplebucket-1250000000/data/warehouse/manifest-2020-01-10.gz
```

>!The command above performs incremental copy only. Only files with size changes can be copied. If the file content is changed, you can refer to the example of `--diffMode` and determine the changed manifest files based on the CRC checksum.

### Obtaining the list of different files and performing incremental copy based on the CRC checksum

Run the command with the `--diffMode` and `--diffOutput` parameters:
- `--diffMode` can be set to `length` or `length-checksum`.
 - `--diffMode=length` obtains the list of different files based on whether the file sizes are the same.
 - `--diffMode=length-checksum` obtains the list of different files based on whether the file size and CRC checksum are the same.
- `--diffOutput` specifies the output directory for the diff operation.

The following example sets `mapred.max.split.size` to 100 KB based on whether the file size and CRC checksum of the source and destination files are the same.

```plaintext
hadoop jar cos-distcp-${version}.jar -Dmapred.max.split.size=102400  --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse/ --diffMode=length-checksum --diffOutput=/tmp/diff-output
```

>!If the destination file system is COS, and the CRC algorithms of the source and destination file systems are different, COSDistCp will pull the source files and calculate the new CRC checksum for CRC checksum comparison.

After the command above is executed, a list of different files will be generated in the `/tmp/diff-output` directory of HDFS. The information about a source file will be contained in the output if at least one of the following is true:

1. A file with the same name does not exist in the destination file system.
2. A file with the same name exists in the destination file system, but has a different file size.
3. A file with the same name exists in the destination file system, but has a different CRC checksum, or the source and destination file systems support different CRC algorithms.

Run the following command to merge the list of different files:

```plaintext
hadoop fs -getmerge /tmp/diff-output diff-manifest
gzip diff-manifest
```

Run the following command to implement incremental copy based on the list of different files:

```plaintext
hadoop  jar cos-distcp-${version}.jar --reducerNumber=20 --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse/ --previousManifest=file:///usr/local/service/hadoop/diff-manifest.gz –copyFromManifest
```

### Specifying the storage class for COS objects

Run the following command with the `--storageClass` parameter:

```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse/ --outputManifest=manifest-2020-01-10.gz --storageClass=STANDARD_IA
```

### Copying metadata of the source file

Run the following command with the `--preserveStatus` parameter. The following command example copies the `user`, `group`, `permission`, and `timestamps` (modification time and access time) metadata of the source file/directory to the destination file/directory:
```plaintext
hadoop jar cos-distcp-${version}.jar --src /data/warehouse --dest cosn://examplebucket-1250000000/data/warehouse/ --preserveStatus=ugpt
```
