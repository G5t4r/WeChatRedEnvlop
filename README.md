# WeChatRedEnvlop
基于猴神的MonkeyDev插件上的抢红包、修改微信步数、非群主@所有人、防止消息撤回插件

## 使用方式
1、从PP助手下载一个破解版的微信直接放入到WeChatRedEnvlop/WeChatRedEnvlop/TargetApp/

2、修改Bundle ID为自己的证书

当然，首先需要安装猴神的MonkeyDev，详见：https://github.com/AloneMonkey/MonkeyDev

微信抢红包插件代码来源于：https://github.com/buginux/WeChatRedEnvelop


自己给自己发消息来控制开关，废话不说了，直接上代码
```objective-c
            if (isMesasgeFromMe)
            {
                if ([m_nsContent rangeOfString:@"打开红包插件"].location != NSNotFound)
                {
                    HBPluginType = kOpenRedEnvPlugin;
                }
                else if ([m_nsContent rangeOfString:@"关闭红包插件"].location != NSNotFound)
                {
                    HBPluginType = kCloseRedEnvPlugin;
                }
                else if ([m_nsContent rangeOfString:@"关闭抢自己红包"].location != NSNotFound)
                {
                    HBPluginType = kCloseRedEnvPluginForMyself;
                }
                else if ([m_nsContent rangeOfString:@"关闭抢自己群红包"].location != NSNotFound)
                {
                    HBPluginType = kCloseRedEnvPluginForMyselfFromChatroom;
                }else if ([m_nsContent rangeOfString:@"修改微信步数#"].location != NSNotFound)
                {
                    NSArray *array = [m_nsContent componentsSeparatedByString:@"#"];
                    if (array.count == 2) {
                        StepCount = ((NSNumber *)array[1]).intValue;
                    }
                } else if([m_nsContent rangeOfString:@"恢复微信步数"].location != NSNotFound) {
                    StepCount = -1;
                }
                //保存修改微信步数设置
                SAVESETTINGS(WeRunStepKey, [NSNumber numberWithInt:StepCount], WeRunSettingFile)
                //保存抢红包设置
                SAVESETTINGS(HBPluginTypeKey, [NSNumber numberWithInt:HBPluginType], HBPluginSettingFile);
            }
```

@所有人的使用方法

```objective-c
#所有人 群发消息
```
