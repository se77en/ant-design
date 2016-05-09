---
order: 0
title: 基本使用
---

基本使用。通过 dataSource 设置自动完成的数据源

````jsx
import { AutoComplete } from 'antd';

const Complete = React.createClass({
  getInitialState() {
    return {
      dataSource: [],
    };
  },
  handleChange(value) {
    const dataSource = value ? [value, value + value, value + value + value] : [];
    this.setState({
      dataSource,
    });
  },
  render() {
    const { dataSource } = this.state;
    return (<AutoComplete dataSource={dataSource}
      style={{ width: 200 }}
      onChange={this.handleChange} />
    );
  },
});
ReactDOM.render(
  <Complete />
, mountNode);
````
