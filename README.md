
# react-radio-group

clone form [react-radio](http://zippyui.github.io/react-radio)

>fix bugs for urgency use

>now only radio type will trigger change event


> A carefully crafted radio-group for React


## Install

```sh
$ npm install react-simple-radio-group
```

## Usage

```jsx
var RadioGroup = require('react-radio')

var colors = [
    {
        value: 'red',
        label: 'Red color',
        style: {
            color: 'red'
        }
    },
    'blue',
    'orange'
]

function onChange(value, event){
    console.log('checked ', value)
}

//uncontrolled
<RadioGroup
    name="colors"
    defaultValue={'red'}
    items={colors}
    onChange={onChange}
/>

var COLOR = 'red'
//controlled
<RadioGroup name="colors" value={COLOR} items={colors} onChange={onChange} />

<RadioGroup name="colors" value={'red'} onChange={onChange}>
    <input type="radio" value="blue" />blue
    <input type="radio" value="red" />red
</RadioGroup>
```

## Props

 * name: String - the name to be set to all radios in the group
 * value/defaultValue - the value that should be checked in the group (controlled/uncontrolled)
 * labelStyle - a style for the radio label
 * inputStyle - a style for the radio input

 * checkedLabelStyle - a style for the checked radio label
 * checkedInputStyle - a style for the checked radio input

 * onChange: Function(value, event) - the function to be calle when the radio group value changes. NOTE: first param sent to this function is the new value, not the event object, as usual

 * renderRadio: Function(props, index, arr) - you can customize how each radio item is rendered in the group using this function. NOTE: it is called with 3 params, so not intended to be directly used with a React factory.

 Example:
 ```jsx
    //NOT LIKE THIS
    <RadioGroup renderRadio={React.DOM.label} />

    //BUT like this
    function renderRadio(props, index, arr){
        return <label {...props} />
    }

    <RadioGroup renderRadio={renderRadio} />

    //or
    function renderRadio(props, index, arr){
        if (index < arr.length - 1){
            props.style.borderBottom = '1px solid blue'
        }
        props.style.display = 'block'
        //we can skip returning something
        //if we only want to modify props/styles
    }
 ```

 If the `renderRadio` function returns undefined, we assume you just wanted to modify the props before rendering, which is ok, so we fallback to the default implementation:
 `<label {...props}/>`

 * items: Array

    The items prop can be an array of strings/objects or mixed. If an array of strings, the strings will be used as both value and label. If objects, `item.value` will be used as a value, and `item.label` as a string:

    Example:
    ```js
        var items = [
            {label: 'Green', value: 'green'},
            {label: 'Blueish', value: 'blue'},
            {value: 'red'} //'red' will be used as both value and label
        ]

        //or
        var items = ['green', 'blue', 'red']
    ```

    If an array item is an object, besides `value` and `label`, it can also have a `style` property and a `checkedStyle` property.

    ```js
    var items = [
        'red',
        {
            label: 'Blue',
            value: 'blue',
            style: { color: 'blue'},
            checkedStyle: { color: 'blue', background: 'red'}
        }
    ]
    ```

 * children - if the component specifies children, the radio group children will not be generated from `items`, but will be what you specify in the `children` prop

If you have a ref to the `react-radio` component, you can also call `group.getValue()` to get the current value of the radio group.


### Contributing
- Fork this Repo first
- Clone your Repo
- Install dependencies by `$ npm install`
- Checkout a feature branch
- Feel free to add your features
- Make sure your features are fully tested
- Publish your local branch, Open a pull request
- Enjoy hacking <3

### MIT license
Copyright (c) 2015 [object Object]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the &quot;Software&quot;), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED &quot;AS IS&quot;, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

---
![docor]()
built upon love by [docor](git+https://github.com/turingou/docor.git) v0.3.0
