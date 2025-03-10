# Switch 开关

### 介绍

用来打开或关闭选项。

### 安装

```js
import { createApp } from 'vue'
import { Switch } from '@nutui/nutui-taro'

const app = createApp()
app.use(Switch)
```

### 基础用法

> demo: switch basic feedback

### 禁用状态

> demo: switch disabled feedback

### 加载状态

> demo: switch loading feedback

### Change 事件

> demo: switch event feedback

### 异步控制

> demo: switch async feedback

### 自定义颜色

> demo: switch color feedback

### 支持文字

> demo: switch text feedback

### 自定义加载图标

> demo: switch icon feedback

## API

### Props

| 参数 | 说明 | 类型 | 默认值 |
| --- | --- | --- | --- |
| v-model | 开关状态 | boolean \| string \| number | `false` |
| disabled `v4.3.2` | 禁用状态 | boolean | `false` |
| loading | 加载状态 | boolean | `false` |
| active-color | 打开时的背景颜色 | string | `#fa2c19` |
| inactive-color | 关闭时的背景颜色 | string | `#ebebeb` |
| active-text | 打开时文字描述 | string | - |
| inactive-text | 关闭时文字描述 | string | - |
| active-value | 打开时组件的值 | boolean ｜ string ｜ number | `true` |
| inactive-value | 关闭组件的值 | boolean ｜ string ｜ number | `false` |
| disable `deprecated` | 禁用状态 | boolean | `false` |

### Slots

| 名称 | 描述 |
| --- | --- |
| icon | loading 状态图标 |

### Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
| change | 切换开关时触发 | (value: boolean,event: Event) |

### 类型定义 v4.3.4

组件导出以下类型定义：

```js
import type {
  SwitchProps,
  SwitchInstance
} from '@nutui/nutui-taro'
```

## 主题定制

### 样式变量

组件提供了下列 CSS 变量，可用于自定义样式，使用方法请参考 [ConfigProvider 组件](#/zh-CN/component/configprovider)。

| 名称 | 默认值 |
| --- | --- |
| --nut-switch-close-bg-color | _#ebebeb_ |
| --nut-switch-close-cline-bg-color | _#f0f0f0_ |
| --nut-switch-width | _36px_ |
| --nut-switch-height | _21px_ |
| --nut-switch-line-height | _21px_ |
| --nut-switch-border-radius | _21px_ |
| --nut-switch-inside-width | _13px_ |
| --nut-switch-inside-height | _13px_ |
| --nut-switch-inside-open-transform | _translateX(146%)_ |
| --nut-switch-inside-close-transform | _translateX(30%)_ |
