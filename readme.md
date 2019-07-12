# 项目插件

|组件名称|作用|备注|
|------|-----|----|
|addressItem|在订单或不同页面显示单条地址信息|NaN|
|themeView|在view中设置主题颜色|NaN|

## 一、addressItem 
### addressInfo的props
|键|值|类型|
|-|-|-|
|addressInfo|{}|Object|

`addressInfo实例`
```javascript
{
    id: 222,//addressId
    realname: "靳建奇",//名字
    mobile: "17724806779",//手机号
    province: "天津市",//省
    city: "天津市",//市
    area: "和平区",//区
    address: "金庸小区",//详细地址
    isdefault: "1",//0非默认1默认
    sex: "0",//0女1男
    type: "0"//0家1公司
}
```
### addressInfo组件的引入
```javascript
//引入页面order.json
{
  "usingComponents": {
    "address-item": "/components/addressItem/index"
  }
}
```

```html
//引入页面order.wxml
<address-item addressInfo='{{addressInfo}}'></address-item>
```

```
//引入页面order.wxss
<address-item addressInfo='{{addressInfo}}'></address-item>
```

```javascript
//引入页面order.js
/** ....其他代码 */
  onShow: function() {
    //如果全局变量中有地址信息，则通过全局变量设置addressInfo
    if (app.globalData.currentAddress) {
      this.setData({
        addressInfo: app.globalData.currentAddress,
        ['orderInfo.address_id']: app.globalData.currentAddress.id
      })
      app.globalData.currentAddress = null;
    } else {
      //否则，通过api获取默认的addressInfo
      this.getDefaultAddress();//此函数中应当设置addressInfo
    }
  }
/** ....其他代码 */
```
### addressItem 样式截图
![addressItem样式](./addressItem.png)