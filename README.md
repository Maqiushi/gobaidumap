gobaidumap
========

百度地图接口调用 golang 版。支持GEO、地址双向获取，IP获取地址。

# 安装/更新

```
go get -u github.com/shajiquan/gobaidumap
```

# 注意
请到百度地图开发者中心申请自己的 App Key，下方的 key 是百度提供的，不保证永远有效。

# 使用

```go
package main

import (
    "fmt"
    "github.com/shajiquan/gobaidumap"
)

func main() {

    var lat string = "40.069462"
    var lng string = "116.346364"

    // 从坐标到地址
    GEOToAddress, err := baidumap.GetAddressViaGEO(lat, lng)

    if err != nil {
        fmt.Println(err)
    }
    fmt.Println("坐标到地址：", GEOToAddress)
    fmt.Println("坐标到地址 - 地址", GEOToAddress.Result.AddressComponent)

    // 从地址到坐标
    address := "百度大厦"
    addressToGEO, err := baidumap.GetGeoViaAddress(address)
    if err != nil {
        fmt.Println(err)
    }

    fmt.Println("从地址到坐标 - All", addressToGEO)
    fmt.Println("从地址到坐标 - Lat", addressToGEO.Result.Location.Lat)
    fmt.Println("从地址到坐标 - Lng", addressToGEO.Result.Location.Lng)

    // 从IP到地址
    ipAddress := "202.198.16.3"
    IPToAddress, err := baidumap.GetAddressViaIP(ipAddress)

    if err != nil {
        fmt.Println(err)
    }
    fmt.Println("从IP到地址：", IPToAddress)
    fmt.Println("从IP到地址 - 地址：", IPToAddress, IPToAddress.Content.Address)

}


```

# 联系 &  反馈

```
shajiquan at gmail dot com

https://github.com/shajiquan/gobaidumap/issues/1
```