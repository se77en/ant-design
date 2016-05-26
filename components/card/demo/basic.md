---
order: 0
title:
  zh-CN: 典型卡片
  en-US: Typical card
---

## zh-CN

包含标题、内容、操作区域。

## en-US

Contains title, content and operating area.

````jsx
import { Card } from 'antd';

ReactDOM.render(
  <Card title="Card title" extra={<a href="#">More</a>} style={{ width: 300 }}>
    <p>Card content</p>
    <p>Card content</p>
    <p>Card content</p>
  </Card>
, mountNode);
````
