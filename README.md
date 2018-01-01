# react-checkbox-group
### A fork from https://github.com/ziad-saab/react-checkbox-group
### Modified and customized for [Lahzenegar](https://lahzenegar.com/)

This is your average checkbox group:

```html
<div class="react-checkbox-group">
  <label><input onChange={this.handleFruitChange} type="checkbox" name="fruit" value="apple" />Apple</label>
  <label><input onChange={this.handleFruitChange} type="checkbox" name="fruit" value="orange" />Orange</label>
  <label><input onChange={this.handleFruitChange} type="checkbox" name="fruit" value="watermelon" />Watermelon</label>
</div>
```

Repetitive, hard to manipulate and easily desynchronized.
Lift up `name` and `onChange`, and give the group an initial checked values array:

```javascript
import {Checkbox, CheckboxGroup} from 'react-checkbox-group';

<CheckboxGroup name="fruits" value={['kiwi', 'pineapple']} onChange={this.fruitsChanged}>
  <Checkbox value="kiwi">Kiwi</Checkbox>
  <Checkbox value="pineapple">Pineapple</Checkbox>
  <Checkbox value="watermelon">Watermelon</Checkbox>
</CheckboxGroup>
```

Listen for changes, get the new value as intuitively as possible:

```javascript
<CheckboxGroup name="fruit" value={['apple','watermelon']} onChange={this.handleChange}>
...
</CheckboxGroup>
```

and further

```javascript
function handleChange(newValues) {
  // ['apple']
}
```

That's it for the API! See below for a complete example.

## Install

```sh
npm install react-checkbox-group
```

Simply require/import it to use it:

```javascript
var Check = require('react-checkbox-group');
var Checkbox = Check.Checkbox;
var CheckboxGroup = Check.CheckboxGroup;

// or ES6
import {Checkbox, CheckboxGroup} from 'react-checkbox-group';
```

## Example

```javascript
class Demo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      fruits: ['apple','watermelon']
    };
  }

  componentDidMount() {
    // Add orange and remove watermelon after 5 seconds
    setTimeout(() => {
      this.setState({
        fruits: ['apple','orange']
      });
    }, 5000);
  }

  render() {
    // the checkboxes can be arbitrarily deep. They will always be fetched and
    // attached the `name` attribute correctly. `value` is optional
    return (
      <CheckboxGroup
        name="fruits"
        value={this.state.fruits}
        onChange={this.fruitsChanged}>

        <Checkbox value="apple"> Apple</Checkbox>
        <Checkbox value="orange"> Orange</Checkbox>
        <Checkbox value="watermelon"> Watermelon</Checkbox>
      </CheckboxGroup>
    );
  }
  
  fruitsChanged = (newFruits) => {
    this.setState({
      fruits: newFruits
    });
  }
  
};

ReactDOM.render(<Demo/>, document.body);
```

## License

MIT.
