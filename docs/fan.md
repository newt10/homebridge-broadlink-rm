# Fan

## Configuration keys and usage
| key | description | example | default |
| -- | -- | -- | -- |
| *name* | Name that you would like to give the device. | Lasko Fan | - |
| *type* | Recognizes device as a fan and parses it accordingly. | fan | fan |
| hideSwingMode | Hide oscillation controls in Home app. | true | false |
| hideRotationDirection | Hide rotation direction controls in Home app. | true | false |
| defaultFanSpeed | Default fan speed to set when turning on device. | 50 | 100 |
| defaultSwingMode | Default oscillation to show in Home app UI when turning on device. | on | off |
| alwaysResetToDefaults | Reset the Home app UI to default state according to defaultFanSpeed and defaultSwingMode. | true | false |
| *data* | Object with hex codes for device operation. | - | - |

### data
| key | description |
| -- | -- |
| *on* | Hex code or object to send for powering on the fan. |
| *off* | Hex code or object to send for powering off the fan. |
| swingOn | Hex code of object to enable fan oscillation. Set to "on" when configuring hex codes for combined fan speed and oscillation. |
| swingOff | Hex code of object to disable fan oscillation. Set to "off" when configuring hex codes for combined fan speed and oscillation. |
| swingToggle | Hex code of object to toggle fan oscillation (use if device accepts a single IR code for enabling and disabling oscillation). |
| clockwise |	A hex code string or object to be sent to make the fan go clockwise. Should be defined when hideRotationDirection is set to false. |
| counterClockwise | A hex code string or object to be sent to make the fan go counter clockwise. Should be defined when hideRotationDirection is set to false. |
| stepSize | Increments of fan speed. This will update Home app UI so that fan speed increases in steps. If your fan support 4 speeds then the step size should be 100/4 = 25. If no values is provided this setting defaults to 1. |
| fanSpeedX | Hex code or object to support set the fan to speed X. |

## FAQ
1. All *italicized* keys are required.
2. This accessory supports combined hex codes for fan speed and oscillation/swing. Please check the config-sample.json file for more details and examples.
3. When hideSwingMode is set to false, either "swingOn/swingOff" OR "swingToggle" must be provided.


## How to set-up config.json
This plugin support fan accessories of different types. Below is an example of building your config.json based on your device.

1. Basic configuration
```
{
	"name": "My Fan",
	"type": "fan",
	"data": {
		"on": "20443...",
		"off": "20443..."
	}
}
```

2. Fan with speed control. In the example below the fan support 2 speeds.
```
{
	"name": "My Fan",
	"type": "fan",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"stepSize": 50,
		"fanSpeed50": "20500..",
		"fanSpeed100": "20500.."
	}
}
```

3. Fan does not memorize last set speed i.e. Powering on the fan resets it to a default speed. In the example below the IR code for data.on will start the fan and set to 50% speed with oscillation disabled and Home app UI will be updated to show correct state. This is recorded by setting up the keys alwaysResetToDefaults, defaultFanSpeed and defaultSwingMode.
```
{
	"name": "My Fan",
	"type": "fan",
	"alwaysResetToDefaults": true,
	"defaultFanSpeed": 50,
	"defaultSwingMode": "off",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"stepSize": 50,
		"fanSpeed50": "20500..",
		"fanSpeed100": "20550.."
	}
}
```

4. Fan with oscillation/swing control and no speed control.
```
{
	"name": "My Fan",
	"type": "fan",
	"alwaysResetToDefaults": true,
	"defaultSwingMode": "off",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"swingOn": "20600..",
		"swingOff": "20660.."
	}
}
```

5. Fan uses a common IR code to enable oscillation/swing at all speeds.
```
{
	"name": "My Fan",
	"type": "fan",
	"alwaysResetToDefaults": true,
	"defaultFanSpeed": 50,
	"defaultSwingMode": "off",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"stepSize": 50,
		"swingOn": "20600...",
		"swingOff": "20660...",
		"fanSpeed50": "20500...",
		"fanSpeed100": "20550..."
	}
}
```

6. Fan uses a common IR code to enable and disable oscillation/swing at all speeds.
```
{
	"name": "My Fan",
	"type": "fan",
	"alwaysResetToDefaults": true,
	"defaultFanSpeed": 50,
	"defaultSwingMode": "off",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"stepSize": 50,
		"swingToggle": "20600...",
		"fanSpeed50": "20500...",
		"fanSpeed100": "20550..."
	}
}
```

7. Fan uses a unique IR code to enable or disable oscillation/swing at all speeds.
```
{
	"name": "My Fan",
	"type": "fan",
	"alwaysResetToDefaults": true,
	"defaultFanSpeed": 50,
	"defaultSwingMode": "off",
	"data": {
		"on": "20443...",
		"off": "20443...",
		"stepSize": 50,
		"swingOn": "on" // this has to be "on"
		"swingOff": "off" // this has to be "off"
		"fanSpeed50": {
			"swingOn": "20500...", // replace with hex codes to turn on swing at the corresponding speed
			"swingOff": "20550..." // replace with hex codes to turn off swing at the corresponding speed
		},
		"fanSpeed100": {
			"swingOn": "20700...",
			"swingOff": "20770..."
		}
	}
}
```