# react-native-printer-status


## Installation:

**Step 1.**

install with npm:

```bash 
npm install https://github.com/cavebring/react-native-printer-status.git --save
```

**Step 2:**

Links this plugin to your project.

```bash
react-native link react-native-printer-status
```

or you may need to link manually 
* modify settings.gradle

```javascript 
include ':react-native-printer-status'
project(':react-native-printer-status').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-printer-status/android')
```

* modify  app/build.gradle,add dependenceie：

```javascript
compile project(':react-native-printer-status')
```

* adds package references to  MainPackage.java 

```java

import com.iposprinter.iposprinterservice.PrinterPackage;
...

 @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(),
            new PrinterPackage()
      );
    }

```

**Step 3:**

refer in the javascript:
```javascript
import PrinterPackage from 'react-native-printer-status';

```

## Usage & Demo:
See examples folder of the source code that you can find a simple example of printing receipt.
// TODO

## API

### Constants
| Name | Description|
|:-----:|:-----------:|
| Constants | 打印状态常量 |
| hasPrinter | boolean,是否有打印机 |
| printerVersion | 打印机固件版本 |
| printerSerialNo | 打印机序列号 |
| printerModal | 打印机型号 |


### Printer Status

|  Name | Description |
|:-----:|:-----------:|
| OUT_OF_PAPER_ACTION | 缺纸异常 |
| ERROR_ACTION | 打印错误 |
| NORMAL_ACTION | 可以打印 |
| COVER_OPEN_ACTION | 开盖子 |
| COVER_ERROR_ACTION | 关盖子异常 |
| KNIFE_ERROR_1_ACTION | 切刀异常1－卡切刀 |
| KNIFE_ERROR_2_ACTION | 切刀异常2－切刀修复 |
| OVER_HEATING_ACITON | 打印头过热异常 |
| FIRMWARE_UPDATING_ACITON | 打印机固件开始升级 |

#### Example

```javascript
import React, { Component } from 'react';
import { View, Text, DeviceEventEmitter } from 'react-native';
import PrinterPackage from 'react-native-printer-status';

class PrinterComponent extends Component {
    componentWillMount() {
        this._printerStatusListener = DeviceEventEmitter.addListener('PrinterStatus', action => {
            switch(action) {
                case PrinterPackage.Constants.NORMAL_ACTION:   // 可以打印
                    // your code
                    break;
                case PrinterPackage.Constants.OUT_OF_PAPER_ACTION:  // 缺纸异常
                    // your code
                    break;
                case PrinterPackage.Constants.COVER_OPEN_ACTION:   // 开盖子
                    // your code
                    break;
                default:
                    // your code
            }
        });
    }
    
    componentWillUnmount() {
        this._printerStatusListener.remove();
    }

    render() {
        return (
            <View>
                <Text>Hello World!</Text>
            </View>
        )
    }
}
```
