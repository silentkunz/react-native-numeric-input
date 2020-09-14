# rn-numeric-input
A cross platform stylish numeric input for react native

This is [react-native-numeric-input](https://www.npmjs.com/package/react-native-numeric-input) package with fixed issues and a new functionality

- dynamically change value using setState ([issue](https://github.com/himelbrand/react-native-numeric-input/issues/45))
- support for custom icons inside plus-minus buttons ([pull request](https://github.com/himelbrand/react-native-numeric-input/pull/62))

<h3 align="center"><b>Visual Demo</b></h3>
<p align="center">
<img src="https://media.giphy.com/media/4To90hOE71mUTgdBVZ/giphy.gif"/>
</p>

## Working example
You can check out the very simple react native example app
Just click [here](https://github.com/himelbrand/react-native-numeric-input/tree/master/Example) and follow the instructions
Enjoy !

## Installation
### Latest version
v1.9.3
#### if you have react-native-vector-icons installed in your project
```bash
yarn add rn-numeric-input
```
or with npm
```bash
npm install rn-numeric-input --save
```
#### if you don't have react-native-vector-icons installed in your project
```bash
yarn add rn-numeric-input react-native-vector-icons
react-native link
```

or with npm

```bash
npm install rn-numeric-input react-native-vector-icons --save
react-native link
```
if you're experiencing issues with `react-native link` which is used to install react-native-vector-icons
please refer to [react-native-vector-icons](https://github.com/oblador/react-native-vector-icons) to see manual installation steps

[link to npm page](https://www.npmjs.com/package/rn-numeric-input)

## Responsive default size

This component uses the [react-native-pixel-perfect](https://www.npmjs.com/package/react-native-pixel-perfect), and the default style is using base resolution for iPhone 7.
In case you want to use the default design but, using a different base resolution, I added a function called updateBaseResolution(width, height).
To use it you need to access it via a ref to the component.

Since the component is dependent on react-native-pixel-perfect, when installing this package you install also react-native-pixel-perfect if it's not already installed.

So you can create your own responsive size function and use it to set your custom style.

## Usage

### import Component
```javascript
import NumericInput from 'rn-numeric-input'
```
### Basic Usage
```javascript
<NumericInput onChange={value => console.log(value)} />
```

**or basic up-down**

```javascript
<NumericInput type='up-down' onChange={value => console.log(value)} />
```
### Keep State Value
```javascript
<NumericInput value={this.state.value} onChange={value => this.setState({value})} />
```
### Advanced Usage
```javascript
        <NumericInput
            value={this.state.value}
            onChange={value => this.setState({value})}
            onLimitReached={(isMax,msg) => console.log(isMax,msg)}
            totalWidth={240}
            totalHeight={50}
            iconSize={25}
            step={1.5}
            valueType='real'
            rounded
            textColor='#B0228C'
            iconStyle={{ color: 'white' }}
            rightButtonBackgroundColor='#EA3788'
            leftButtonBackgroundColor='#E56B70'/>
```


## Props
Name                                | Type                                | Default
------------------------------------|-------------------------------------|:-------:
**value**                           |`number`                             | none
**minValue**                        |`number`                             | none
**maxValue**                        |`number`                             | none
**step**                            |`number`                             | 1
**valueType**                       |`'integer'` or `'real'`                  | `'integer'`
**initValue**                       |`number`                             | null if not used will start at 0
**iconSize**                        |`number`                             | calcSize(30)
**borderColor**                     |`string`                             | `'#d4d4d4'`
**iconStyle**                       |`object`                             | none
**totalWidth**                      |`number`                             | calcSize(220)
**separatorWidth**                   |`number`                             | 1
**type**                            |`'plus-minus'` or `'up-down'`        | `'plus-minus'`
**rounded**                         |`boolean`                            | false
**textColor**                       |`string`                             | `'black'`
**containerStyle**                  |`object`                             | none
**inputStyle**                      |`object`                             | none
**upDownButtonsBackgroundColor**    |`string`                             | `'white'`
**rightButtonBackgroundColor**      |`string`                             | `'white'`
**leftButtonBackgroundColor**       |`string`                             | `'white'`
**customDecIcon**                   |`element` or `node`                  | none
**customIncIcon**                   |`element` or `node`                  | none
**totalHeight**                     |`number`                             | none
**onChange**                        |`function`                           | none - required prop
**onLimitReached**                  |`function`                           | none (empty function)
**editable**                        |`boolean`                            | true
**validateOnBlur**                  |`boolean`                            | true
**reachMaxIncIconStyle**            |`object`                             | none
**reachMaxDecIconStyle**            |`object`                             | none
**reachMinIncIconStyle**            |`object`                             | none
**reachMinDecIconStyle**            |`object`                             | none
**extraTextInputProps**             |`object`                             | none

### notes about props

* **value prop** - this component uses it's own state to hold value if value is not given as a prop
* **style props** - this component has a default style and the styles props are to override the default style or add more fields
* **totalWidth prop** - this prop is for the entire component width, and all other sizes are derived from it , unless given other size props
* **initValue prop** - if using value prop, this is not needed and the initial value can be given by the value prop
* **validateOnBlur** - added on version 1.3.2, if set to false the text input will validate while typing, not recommended, so just keep it true unless there is a good reason not to use the default functionality
* **reachMaxIncIconStyle** - added on version 1.4.0, used to set style to the increment button icon in case maxValue is reached - **optional**
* **reachMaxDecIconStyle** - added on version 1.4.0, used to set style to the decrement button icon in case maxValue is reached - **optional**
* **reachMinIncIconStyle** - added on version 1.4.0, used to set style to the increment button icon in case minValue is reached - **optional**
* **reachMinDecIconStyle** - added on version 1.4.0, used to set style to the decrement button icon in case minValue is reached - **optional**
* **onLimitReached** - added on version 1.7.0, used to handle event of min/max reached, **this function receives 2 arguments: (isMax:Boolean, msg:String)** like in the advanced example above - **optional**
* **extraTextInputProps**  - added on version 1.8.0, used to add props used for the original TextInput component that are not used/supported in this component explicitly - **optional**
*  **customDecIcon** & **customIncIcon** - added on version 1.9.0, used for custom icons inside `'plus-minus'` buttons - **optional**

## License
This project is licensed under the MIT License
