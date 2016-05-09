---
order: 1
title: dataSource 为对象
---

`dataSource` 的每一项为一个对象。


````jsx
import { AutoComplete } from 'antd';

const Complete = React.createClass({
  getInitialState() {
    return {
      dataSource: [],
    };
  },
  handleChange(value) {
    let dataSource;
    if (!value || value.indexOf('@') >= 0) {
      dataSource = [];
    } else {
      dataSource = ['gmail.com', '163.com', 'qq.com'].map(domain => {
        const email = `${value}@${domain}`;
        return { text: email, value: email };
      });
    }
    this.setState({ dataSource });
    console.log(`selected ${value}`);
  },
  render() {
    const { dataSource } = this.state;
    return (<AutoComplete dataSource={dataSource}
      style={{ width: 200 }}
      allowClear
      onChange={this.handleChange} />
    );
  },
});
ReactDOM.render(
  <Complete />
, mountNode);
````
