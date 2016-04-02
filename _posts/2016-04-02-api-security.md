---
layout: inner
position: right
title: 'api security'
date: 2016-04-02 13:14:00
categories: development
tags: API SECURITY
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'API SECURITY'
---

# API SECURITY

---

## Http/Https

	HTTP 超文本传输协议，是一种明文传输过程，数据都可以抓包出来。
	HTTPS 超文本传输安全协议，利用SSL/TLS来对数据包进行加密，数据都是以加密形式传输。

## Security

	关于请求安全，需要考虑两个部分，一是应用层安全，二是运输层安全。

	应用层安全，可以预防api被利用，数据可以多加一层数据加密和检测之类，或者是达到控制某某版本可用，不可用的状态。

	运输层安全，现在一般都是使用SSL/TLS来对数据包进行加密。

	在这里主要考虑应用层这一块。

## Request

	app_id: 1
	timestamp: 1459576215
	version: 20160402
	sign: md5(secretKey + sort(params))

	app_id 可作为每个接入app使用不同的secretKey
	timestamp 毫秒时间，保证每次请求参数的md5都是不同的结果。
	version 固定的时间版本号，可以作为版本控制，不同版本可能使用不同的secretKey。
	sign 签名，客户端通过请求参数的md5结果，服务端收到参数后再进行一次运算，如果一致请求有效。

## Example(golang)

	/users?app_id=1&timestamp=1459576215&version=20160402&sign=3a4d50aa499cc0c066c8c670b1d3118d

	package main

	import (
		"crypto/md5"
		"encoding/hex"
		"fmt"
		"sort"
	)

	const (
		API_SECRET_KEY = "ddc5f5e86d2f85e1b1ff763aff13ce0a"
	)

	func paramsWithoutSign(values map[string]string) (params string) {
		var keys []string
		for k, _ := range values {
			if k != "sign" {
				keys = append(keys, k)
			}
		}
		sort.Strings(keys)
		for _, k := range keys {
			params += fmt.Sprintf("%s=%s&", k, values[k])
		}
		return
	}

	func sign(params string) (sign string) {
		h := md5.New()
		h.Write([]byte(API_SECRET_KEY + params))
		sign = hex.EncodeToString(h.Sum(nil))
		return
	}

	func main() {

		values := make(map[string]string)
		values["app_id"] = "1"
		values["timestamp"] = "1459576215"
		values["version"] = "20160402"
		values["sign"] = "3a4d50aa499cc0c066c8c670b1d3118d"

		params := paramsWithoutSign(values)
		sign := sign(params)

		fmt.Println(params)
		fmt.Println(sign)

		if sign == values["sign"] {
			fmt.Println("ok")
		} else {
			fmt.Println("fail")
		}

	}



