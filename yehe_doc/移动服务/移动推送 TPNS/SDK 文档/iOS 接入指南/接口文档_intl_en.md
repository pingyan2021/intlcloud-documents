## Description

The account, tag, and user attribute features in this document are applicable to **SDK v1.2.9.0 and above**. For **v1.2.7.2** and below, please see [API Documentation](https://intl.cloud.tencent.com/document/product/1024/30727).



## Launching TPNS Service
The following are device registration API methods. For more information on the timing and principle of calls, please see [Overview](https://intl.cloud.tencent.com/document/product/1024/30725).
#### API description

This API is used to launch the TPNS service by using the information of the application registered at the official website of TPNS.
(This API is newly added in SDK v1.2.7.2. For v1.2.7.1 and below, please see the `startXGWithAppID` API in the `XGPush.h` file in the SDK package.)

```objective-c
/// @note TPNS SDK1.2.7.2+
- (void)startXGWithAccessID:(uint32_t)accessID accessKey:(nonnull NSString *)accessKey delegate:(nullable id<XGPushDelegate>)delegate;
```

#### Parameter description

- accessID: `AccessID` applied through the frontend.
- accessKey: `AccessKey` applied through the frontend.
- Delegate: callback object. 

>!The parameters required by the API must be entered correctly; otherwise, TPNS will not be able to push messages correctly for the application.

#### Sample code

```Objective-C
 [[XGPush defaultManager] startXGWithAccessID:<your AccessID> accessKey:<your AccessKey> delegate:self];
```

## Ending TPNS Service
The following are device unregistration API methods. For more information on the timing and principle of calls, please see [Overview](https://intl.cloud.tencent.com/document/product/1024/30725).
#### API description

After the TPNS service is stopped, the application will not be able to push messages to devices through TPNS. To receive messages pushed by TPNS again, you must call the `startXGWithAccessID:accessKey:delegate:` method again to restart the TPNS service.

```objective-c
- (void)stopXGNotification;
```

#### Sample code

```Objective-C
[[XGPush defaultManager] stopXGNotification];
```



## TPNS Token and Registration Result

### Querying TPNS token

#### API description

This API is used to query the token string generated by the current application on the TPNS server.

```objective-c
@property (copy, nonatomic, nullable, readonly) NSString *xgTokenString;
```

#### Sample code

```objective-c
NSString *token = [[XGPushTokenManager defaultTokenManager] xgTokenString];
```

### Registration result callback

#### API description

After the SDK is started, use this method callback to return the registration result and token.

```objective-c
- (void)xgPushDidRegisteredDeviceToken:(nullable NSString *)deviceToken xgToken:(nullable NSString *)xgToken error:(nullable NSError *)error
```

#### Response parameter description

- deviceToken: `Device Token` generated by APNs.
- xgToken: `Token` generated by TPNS, which needs to be used during message push. TPNS maintains the mapping relationship between this value and the `Device Token` of APNs.
- error: error message. If `error` is `nil`, the push service has been successfully registered.

### Registering failure callback

#### API description

This callback is new in SDK 1.2.7.2 and used for TPNS registration failures.

```objective-c
/// @note TPNS SDK1.2.7.2+
- (void)xgPushDidFailToRegisterDeviceTokenWithError:(nullable NSError *)error
```

## Account Feature
The following are account API methods. For more information on the timing and principle of calls, please see [Overview](https://intl.cloud.tencent.com/document/product/1024/30725).
### Adding account
#### API description

If there is no account of this type, this API will add a new one; otherwise, it will overwrite the existing one. (Newly added in TPNS SDK v1.2.9.0+)
```Objective-C
- (void)upsertAccountsByDict:(nonnull NSDictionary<NSNumber *, NSString *> *)accountsDict;
```

>?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.



#### Parameter description 


- accountsDict: account dictionary.

>?
>- The account type and account name together serve as the composite primary key.
>- You need to use the dictionary type, where `key` is the account type and `value` is the account, such as @{@(accountType):@"account"}.
>- Syntax for Objective-C: @{@(0):@"account0",@(1):@"account1"}; syntax for Swift: [NSNumber(0):@"account0",NSNumber(1):@"account1"].
>- For more `accountType` values, please see the enumerated values of `XGPushTokenAccountType` in the `XGPush.h` file in the SDK package.


#### Sample code


```Objective-C
XGPushTokenAccountType accountType = XGPushTokenAccountTypeUNKNOWN;
NSString *account = @"account";
[[XGPushTokenManager defaultTokenManager] upsertAccountsByDict:@{ @(accountType):account }];
```


### Deleting account
#### API description

API description: this API is used to delete all accounts in the specified account type. (Newly added in TPNS SDK 1.2.9.0+)

```Objective-C
- (void)delAccountsByKeys:(nonnull NSSet<NSNumber *> *)accountsKeys;
```

>?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.


#### Parameter description 


- accountsKeys: set of account types.

>?
>- A set is required, and the key is fixed.
>- For more `accountType` values, please see the enumerated values of `XGPushTokenAccountType` in the `XGPush.h` file in the SDK package.


#### Sample code


```Objective-C
XGPushTokenAccountType accountType = XGPushTokenAccountTypeUNKNOWN;

NSSet *accountsKeys = [[NSSet alloc] initWithObjects:@(accountType), nil];

[[XGPushTokenManager defaultTokenManager] delAccountsByKeys:accountsKeys];
```


### Clearing all accounts

#### API description

This API is used to clear all the set accounts.

```Objective-C
- (void)clearAccounts;
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] clearAccounts];
```
## Tagging Feature
The following are tag API methods. For more information on the timing and principle of calls, please see [Overview](https://intl.cloud.tencent.com/document/product/1024/30725).
### Binding/Unbinding tag

#### API description

You can bind tags to different users and then push based on a specific tag.

```Objective-C
- (void)appendTags:(nonnull NSArray<NSString *> *)tags
- (void)delTags:(nonnull NSArray<NSString *> *)tags
```

> ?
> - This API works in an appending manner.
> - This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.
> - One application can have up to 10,000 custom tags. One device token can be bound to up to 100 custom tags (if you want to increase this limit, please [submit a ticket](https://console.cloud.tencent.com/workorder/category)). One custom tag can be bound to an unlimited number of device tokens.

#### Parameter description

- tags: tag array.

> ?For tag operations, `tags` is a tag string array (the tag string cannot contain spaces or tabs).

#### Sample code

```Objective-C
// Bind the tag:
[[XGPushTokenManager defaultTokenManager] appendTags:@[ tagStr ]];

// Unbind the tag
[[XGPushTokenManager defaultTokenManager] delTags:@[ tagStr ]];
```



### Updating tag

#### API description

This API is used to clear all the existing tags and then add tags in batches.

```Objective-C
- (void)clearAndAppendTags:(nonnull NSArray<NSString *> *)tags
```

> ?
> - This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.
> - This API will replace all the old tags corresponding to the current token with the current tag.

#### Parameter description 

- tags: tag array.

> ?For tag operations, `tags` is a tag string array (the tag string cannot contain spaces or tabs).



#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] clearAndAppendTags:@[ tagStr ]];
```

### Clearing all tags

#### API description

This API is used to clear all the set tags.

```Objective-C
- (void)clearTags
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] clearTags];
```

## User Attribute Feature
The following are user attribute API methods. For more information on the timing and principle of calls, please see [Overview](https://intl.cloud.tencent.com/document/product/1024/30725).
### Adding user attribute

#### API description

This API is used to add or update user attributes in the `key-value` structure (if there is no user attribute value corresponding to the key, it will add a new one; otherwise, it will update the value).

```Objective-C
- (void)upsertAttributes:(nonnull NSDictionary<NSString *,NSString *> *)attributes
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Parameter description 

- attributes: user attribute string dictionary. The string cannot contain spaces or tabs.

> ? 
> - You need to configure the user attribute keys in the console first before the operation can succeed.
> - A dictionary array is required, and the key is fixed.
> - Syntax for Objective-C: @{@"gender": @"Female", @"age": @"29"};
> - Syntax for Swift: ["gender":"Female", "age": "29"]

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] upsertAttributes:attributes];
```

### Deleting user attribute

#### API description

This API is used to delete the existing user attributes.

```Objective-C
- (void)delAttributes:(nonnull NSSet<NSString *> *)attributeKeys
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Parameter description 

- attributeKeys: set of user attribute keys. The string cannot contain spaces or tabs.

> ?A set is required, and the key is fixed.

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] delAttributes:attributeKeys];
```

### Clearing all user attributes

#### API description

This API is used to clear all the existing user attributes.

```Objective-C
- (void)clearAttributes;
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] clearAttributes];
```

### Updating user attribute

#### API description

This API is used to clear all the existing user attributes and then add user attributes in batches.



```Objective-C
- (void)clearAndAppendAttributes:(nonnull NSDictionary<NSString *,NSString *> *)attributes
```

> ?This API should be called after `xgPushDidRegisteredDeviceToken:error:` returns a success.

#### Sample code

```Objective-C
[[XGPushTokenManager defaultTokenManager] clearAndAppendAttributes:attributes];
```

## Badge Feature

### Syncing badge

#### API description

When the local badge number is changed for the application, you need to call this API to sync it to the TPNS server, which will be used as the basis for the next push. This feature is in the console > **Create Push** > **Advanced Settings** > **Badge Number**.

```objective-c
- (void)setBadge:(NSInteger)badgeNumber;
```

#### Parameter description

badgeNumber: badge number of application.

> ! When the local badge number is set for the application, you need to call this API to sync it to the TPNS server, which will take effect in the next push. This API must be called after successful TPNS registration (xgPushDidRegisteredDeviceToken).

#### Sample code
```Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    /// Zero the badge number every time the application is started (you should set the local badge number for the application in the main thread)
    if ([XGPush defaultManager].xgApplicationBadgeNumber > 0) {
        [XGPush defaultManager].xgApplicationBadgeNumber = 0;
    }
    return YES;
}

- (void)xgPushDidRegisteredDeviceToken:(nullable NSString *)deviceToken xgToken:(nullable NSString *)xgToken error:(nullable NSError *)error {
    /// Sync the badge number to TPNS after registration
    if (!error) {
        [[XGPush defaultManager] setBadge:0];
    }
}
```



## Querying Device Notification Permission

#### API description

This API is used to query whether the user allows device notification. 

```objective-c
- (void)deviceNotificationIsAllowed:(nonnull void (^)(BOOL isAllowed))handler;
```

#### Parameter description

handler: return method of query result.

#### Sample code

```objective-c
[[XGPush defaultManager] deviceNotificationIsAllowed:^(BOOL isAllowed) {
        <#code#>
    }];
```

## Querying SDK Version

#### API description

This API is used to query the current SDK version.

```objective-c
- (nonnull NSString *)sdkVersion;
```

#### Sample code

```objective-c
[[XGPush defaultManager] sdkVersion];
```

## Log Reporting APIs

#### API description

If you find exceptions with push, you can call this API to trigger reporting of local push logs. When [submitting a ticket](https://console.cloud.tencent.com/workorder/category) to report the problem, please provide the file address for us to troubleshoot.

```
/// @note TPNS SDK1.2.4.1+
- (void)uploadLogCompletionHandler:(nullable void(^)(BOOL result,  NSString * _Nullable errorMessage))handler;
```

#### Parameter description

- @brief: report log information (SDK 1.2.4.1+).
- @param handler: report callback.

#### Sample code

```
[[XGPush defaultManager] uploadLogCompletionHandler:nil];
```


## TPNS Log Hosting

#### API description

You can get TPNS logs by using this method, which has nothing to do with `XGPush > enableDebug`.

#### Parameter description

- logInfo: log information.

#### Sample code

```
- (void)xgPushLog:(nullable NSString *)logInfo;
```

## Customizing Notification Bar Message Action

### Creating message action

#### API description

This API is used to create a clickable event action in the notification message.

```objective-c
+ (nullable id)actionWithIdentifier:(nonnull NSString *)identifier title:(nonnull NSString *)title options:(XGNotificationActionOptions)options;
```

#### Parameter description

- identifier: unique action ID. 
- title: action name. 
- options: options supported by action.

#### Sample code

```objective-c
XGNotificationAction *action1 = [XGNotificationAction actionWithIdentifier:@"xgaction001" title:@"xgAction1" options:XGNotificationActionOptionNone];
```

> !The notification bar has the click event feature, which is only supported in iOS 8.0+. For iOS 7.x or earlier, this method will return null.

### Creating category object

#### API description

This API is used to create a category object to manage the action object of the notification bar.

```objective-c
+ (nullable id)categoryWithIdentifier:(nonnull NSString *)identifier actions:(nullable NSArray<id> *)actions intentIdentifiers:(nullable NSArray<NSString *> *)intentIdentifiers options:(XGNotificationCategoryOptions)options
```

#### Parameter description

- identifier: category object ID.
- actions: action object group owned by the current category.
- intentIdentifiers: used to indicate identifiers that can be recognized by Siri.
- options: category characteristics.

> !The notification bar has the click event feature, which is only supported in iOS 8+. For iOS 8 or earlier, this method will return null.

#### Sample code

```Objective-C
XGNotificationCategory *category = [XGNotificationCategory categoryWithIdentifier:@"xgCategory" actions:@[action1, action2] intentIdentifiers:@[] options:XGNotificationCategoryOptionNone];
```

### Creating configuration class

#### API description

This API is used to manage the style and characteristics of the push message notification bar.

```objective-c
+ (nullable instancetype)configureNotificationWithCategories:(nullable NSSet<id> *)categories types:(XGUserNotificationTypes)types;
```

#### Parameter description

- categories: collection of categories supported by the notification bar. 
- types: style of registered notification.

#### Sample code

```objective-c
XGNotificationConfigure *configure = [XGNotificationConfigure configureNotificationWithCategories:[NSSet setWithObject:category] types:XGUserNotificationTypeAlert|XGUserNotificationTypeBadge|XGUserNotificationTypeSound];
```

## Local Push

For local push features, please see [Apple developer documentation](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SchedulingandHandlingLocalNotifications.html#//apple_ref/doc/uid/TP40008194-CH5-SW1).

