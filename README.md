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
| Constants | 
| hasPrinter |
| printerVersion |
| printerSerialNo | 
| printerModal |


### Printer Status

|  Name | Description |
|:-----:|:-----------:|
| NORMAL_ACTION | 
| PAPERLESS_ACTION | 
| PAPEREXISTS_ACTION | 
| THP_HIGHTEMP_ACTION | 
| THP_NORMALTEMP_ACTION | 
| MOTOR_HIGHTEMP_ACTION | 
| BUSY_ACTION | 
| CURRENT_TASK_PRINT_COMPLETE_ACTION | 


#### Example

```javascript
import React, { Component } from 'react';
import { View, Text, DeviceEventEmitter } from 'react-native';
import PrinterPackage from 'react-native-printer-status';

class PrinterComponent extends Component {
    componentWillMount() {
        this._printerStatusListener = DeviceEventEmitter.addListener('PrinterStatus', action => {
            switch(action) {
                case PrinterPackage.Constants.PAPERLESS_ACTION: 
                    // your code
                    break;
                case PrinterPackage.Constants.THP_HIGHTEMP_ACTION:  
                    // your code
                    break;
                case PrinterPackage.Constants.MOTOR_HIGHTEMP_ACTION:  
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
