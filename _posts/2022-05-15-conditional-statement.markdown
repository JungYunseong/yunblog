---
layout: post
title:  조건문
date:   2022-05-15 00:00:00 +0300
image:  '/images/post/Conditional Statement/conditionalStatement1.jpg'
tags:   [SwiftUI, Development]
---
# Swift에서 조건문을 표현하는 방법

## if문 사용

- () 사용

```swift
if (isActivated == false) {
                Text("비활성화 상태입니다")
                    .foregroundColor(Color.gray)
                    .padding()
            } else {
                Text("활성화 상태입니다")
                    .foregroundColor(Color.green)
                    .padding()
            }
```
<br/>

- () 미사용

```swift
if isActivated == false {
                Text("비활성화 상태입니다")
                    .foregroundColor(Color.gray)
                    .padding()
            } else {
                Text("활성화 상태입니다")
                    .foregroundColor(Color.green)
                    .padding()
            }
```
<br/>

- ! 사용

```swift
if isActivated != true {
                Text("비활성화 상태입니다")
                    .foregroundColor(Color.gray)
                    .padding()
            } else {
                Text("활성화 상태입니다")
                    .foregroundColor(Color.green)
                    .padding()
            }
```
<br/>

- == 미사용

```swift
if isActivated {
                Text("활성화 상태입니다")
                    .foregroundColor(Color.green)
                    .padding()
            } else {
                Text("비활성화 상태입니다")
                    .foregroundColor(Color.gray)
                    .padding()
            }
```
<br/>

- == 미사용, ! 사용
<a name="TO"></a>

```swift
if !isActivated {
                Text("비활성화 상태입니다")
                    .foregroundColor(Color.gray)
                    .padding()
            } else {
                Text("활성화 상태입니다")
                    .foregroundColor(Color.green)
                    .padding()
            }
```
<br/>

## 삼항연산자 사용

- () 사용

```swift
Text((isActivated == true) ? "활성화 상태입니다" : "비활성화 상태입니다")
                .foregroundColor((isActivated == true) ? Color.green : Color.gray)
                    .padding()
```
<br/>

- () 미사용

```swift
Text(isActivated == true ? "활성화 상태입니다" : "비활성화 상태입니다")
                .foregroundColor(isActivated == true ? Color.green : Color.gray)
                    .padding()
```
<br/>

- ! 사용

```swift
Text(isActivated != true ? "비활성화 상태입니다" : "활성화 상태입니다")
                .foregroundColor(isActivated != true ? Color.gray : Color.green)
                    .padding()
```
<br/>

- == 미사용

```swift
Text(isActivated ? "활성화 상태입니다" : "비활성화 상태입니다")
                .foregroundColor(isActivated ? Color.green : Color.gray)
                    .padding()
```
<br/>

- == 미사용, !사용

```swift
Text(!isActivated ? "비활성화 상태입니다" : "활성화 상태입니다")
                .foregroundColor(!isActivated ? Color.gray : Color.green)
                    .padding()
```

***