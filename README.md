# Homebridge Broadlink RM Enhanced

## Introduction
Welcome to the Broadlink RM Mini and Broadlink RM Pro plugin for [Homebridge](https://github.com/nfarina/homebridge).

This is a fork of the [original plugin by Luke Rhodes] (https://github.com/lprhodes/homebridge-broadlink-rm) that allows you to control your RM Mini and RM Pro with HomeKit using the Home app and Siri.

### About this fork
I am working on upgrades to the accessory specifications in this repository. For starters I am focused on fan, air-conditioners and heater accessories to help improve the user experience of the devices like portable ACs, Lasko tower fans and tower heaters, etc.

I eventually would like to add multiple contibuters who can review and integrate PRs so more people can collectively extend the accessories.

If you want to use this fork, use this command:

`npm i -g homebridge-broadlink-rm-enhanced`

This plugin can be used in conjunction with other forks of Broadlink RM plugin. This enables one to use this plugin for some accessories while other plugin for other accessories with the same Broadlink IR Blaster.

## What's new
For updates to the plugin please review the [changelog](https://github.com/newt10/homebridge-broadlink-rm-enhanced/blob/master/Changelog.md)

## Like this plugin?

Please consider testing it and providing feedback. Supporting this project is defintely a lot of work due to the various types of devices that can be interfaced with this. If you are finding value from this plugin please consider supporting it by buying me a coffee using [Paypal](https://paypal.me/MahavirParekh).

Thank you!

## Documentation

### Orignial
Full documentation can be found [here](https://lprhodes.github.io/slate/).

Use [config-sample.json](https://github.com/newt10/homebridge-broadlink-rm-enhanced/blob/master/config-sample.json) file for plugin specific config changes.

### Enhancements

The platform has been renamed compared to the original so that you can install this plugin alongside the original plugin or other forks.
```
{
	"platform": "BroadlinkRM-Enhanced"
}
```

#### Fan Accessory
##### Fan speed step size property
Improves user experience of changing fan speeds to pre-defined steps in the Home app.

<img src="https://j.gifs.com/L7oJQX.gif" alt="Home app fan speed UI in action" width="150"/>

##### Combined fan speed and swing modes
Some fans (e.g. Lasko tower fan) with remotes that have a display, generate unique hex codes for a combination of each speed and swing mode. If you have such a device, you can record each hex code in the config.json.

##### Default swing mode
When using alwaysResetToDefaults, you can add a parameter to let the system know the default oscillation mode.

For more details on how to configure a fan accessory please review the documentation [here](https://github.com/newt10/homebridge-broadlink-rm-enhanced/blob/master/docs/fan.md)

#### Heater Cooler Accessory
Implementation of heater cooler accessory specification as per Apple HAP. Heater cooler allows for better representation of standalone heaters and air-conditioners that support functions like 
oscillation and fan speed.

In addition to the fan speed and oscillation features, this accessory also supports temperature in both degree Celsius and Fahrenheit.

<img src="https://j.gifs.com/vlVRR0.gif" alt="Home app heater cooler UI in action" width="150"/>

For more details on how to configure a heater-cooler accessory please review the documentation [here](https://github.com/newt10/homebridge-broadlink-rm-enhanced/blob/master/docs/heater-cooler.md) and review [config-sample.json](https://github.com/newt10/homebridge-broadlink-rm-enhanced/blob/master/config-sample.json) for sample configurations.


## Thanks
Thanks to @lprhodes (https://github.com/lprhodes/homebridge-broadlink-rm), @kiwi-cam (https://github.com/kiwi-cam/homebridge-broadlink-rm), @tattn (https://github.com/tattn/homebridge-rm-mini3), @PJCzx (https://github.com/PJCzx/homebridge-thermostat) @momodalo (https://github.com/momodalo/broadlinkjs) whose time and effort got me started.
