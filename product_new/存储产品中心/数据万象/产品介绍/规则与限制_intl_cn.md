| 功能 |限制说明|
|-------|---------|
|图片处理|<li>支持格式：目前支持处理 JPG、BMP、GIF、PNG、WEBP、SVG、PSD 格式，并且支持 HEIF 格式的解码和处理。<li>体积限制：图片大小不超过20MB，图片宽高不超过9999像素。|
| [格式转换](https://intl.cloud.tencent.com/document/product/1045/33716) |支持 JPG，BMP， GIF，PNG，WEBP，YJPEG，缺省为原图格式。|
| [质量变换](https://intl.cloud.tencent.com/document/product/1045/33717) |仅针对 JPG 和 WEBP 格式图片。|
| [渐进显示](https://intl.cloud.tencent.com/document/product/1045/33716) |仅支持 JPG 格式，如果输出非 JPG 图片格式，会忽略该参数。|
|[高斯模糊](https://intl.cloud.tencent.com/document/product/1045/33718)|不支持 GIF 格式图片。|
|[管道操作符](https://intl.cloud.tencent.com/document/product/1045/33727)|可实现对图片按顺序进行多种处理，目前最多支持三层管道。|


>数据万象基于 COS 对象存储，关于存储及上传规格的限制请参见 [COS 规格与限制](https://intl.cloud.tencent.com/document/product/436/14518)。