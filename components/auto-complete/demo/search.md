---
order: 4
title: 搜索框
---

 带有搜索按钮的自动补全输入框

````jsx
import { AutoComplete, Input, Button } from 'antd';
import jsonp from 'jsonp';
import classNames from 'classnames';
import querystring from 'querystring';

const Complete = React.createClass({
  getInitialState() {
    return {
      dataSource: [],
    };
  },
  fetch(value, callback) {
    const str = querystring.encode({
      code: 'utf-8',
      q: value,
    });
    if (this.timeout) {
      clearTimeout(this.timeout);
    }
    this.timeout = setTimeout(() => {
      jsonp(`http://suggest.taobao.com/sug?${str}`, (err, data) => {
        callback(data.result.map(d => {
          return {
            text: d[0],
            value: d[0],
          };
        }));
      });
    }, 300);
  },
  handleChange(value) {
    this.fetch(value, dataSource => this.setState({ dataSource }));
    console.log('AutoComplete change', value);
  },
  render() {
    const { dataSource } = this.state;
    const { style, size } = this.props;
    const btnCls = classNames({
      'ant-search-btn': true,
    });
    const searchCls = classNames({
      'ant-search-input': true,
    });

    return (
      <div className="ant-search-input-wrapper" style={style}>
        <Input.Group className={searchCls}>
          <AutoComplete
            dataSource={dataSource}
            onChange={this.handleChange} />
          <div className="ant-input-group-wrap">
            <Button icon="search" className={btnCls} size={size} onClick={this.handleSearch} />
          </div>
        </Input.Group>
      </div>
    );
  },
});
ReactDOM.render(
  <Complete style={{ width: 200 }} />
, mountNode);
````

````css
.code-box-demo .ant-select {
  margin: 0 8px 10px 0;
}
````