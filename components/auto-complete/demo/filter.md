---
order: 3
title: 过滤器
---

Autocomplete 同样可以使用 filterOption

````jsx
import { AutoComplete } from 'antd';

const Complete = React.createClass({
  getInitialState() {
    return {
      dataSource: ['Red', 'Orange', 'Yellow'],
    };
  },
  filterOption(inputValue, option) {
    return option.props.children.toLowerCase().indexOf(inputValue.toLowerCase()) !== -1;
  },
  render() {
    const { dataSource } = this.state;
    return (<AutoComplete style={{ width: 200 }}
      dataSource={dataSource}
      filterOption={this.filterOption} />
    );
  },
});
ReactDOM.render(
  <Complete />
, mountNode);
````
