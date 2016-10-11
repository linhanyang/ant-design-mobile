---
order: 1
title: 向上弹出效果
---

Popup 向上弹出效果

````jsx
import { Popup, List, Button, Icon } from 'antd-mobile';

const Test = React.createClass({
  getInitialState() {
    return {
      sel: '',
    };
  },
  onClick() {
    Popup.show(<div>
      <List renderHeader={() => (
        <div style={{ position: 'relative' }}>
          委托买入
          <span
            style={{
              position: 'absolute', right: 3, top: -5,
            }}
            onClick={() => this.onClose('cancel')}
          >
            <Icon type="cross" />
          </span>
        </div>)
      }
      >
        <List.Item>股票名称</List.Item>
        <List.Item>股票代码</List.Item>
        <List.Item>买入价格</List.Item>
        <List.Item>买入数量</List.Item>
      </List>
      <ul style={{ padding: '0.18rem 0.3rem' }}>
        <li>投资说明投资说明...</li>
        <li style={{ marginTop: '0.18rem' }}>
          <Button type="primary" onClick={() => this.onClose('cancel')}>买入</Button>
        </li>
      </ul>
    </div>, { animationType: 'slide-up' });
  },
  onClose(sel) {
    this.setState({ sel });
    Popup.hide();
  },
  render() {
    return (<div style={{ padding: '15px' }}>
      <Button type="ghost" onClick={this.onClick}>显示</Button>
    </div>);
  },
});

ReactDOM.render(<Test />, mountNode);
````