---
layout: post
title:  Activity views, Share sheets
date:   2022-05-22 00:00:00 +0300
image:  '/images/post/activity view/activityView.jpg'
tags:   [SwiftUI, UIKit, HIG, Development]
---
> An activity is a task, such as Copy, Favorite, or Find, that’s useful in the current context.
>
> <cite><a href="https://papago.naver.net/website?locale=ko&source=en&target=ko&url=https%3A%2F%2Fdeveloper.apple.com%2Fdesign%2Fhuman-interface-guidelines%2Fios%2Fviews%2Factivity-views%2F" target="_blank">Human Interface Guideline</a></cite>

각 Activity들은 activity view에 의해 관리되고 기기나 기기의 방향에 따라 시트 또는 팝오버로 표시됩니다. 서비스 또는 앱에서 작업에 대한 커스텀을 할 수 있게 사용자에게 액세스 권한은 부여하는 활동을 사용합니다. <br/><br/>
이 시스템은 인쇄, 메시지, AirPlay 등 다양한 활동을 제공합니다. 이러한 task들은 activity view에 먼저 나타나며 순서를 변경할 수 없습니다. 또, 기본으로 제공되기 때문에 직접 커스텀 할 필요가 없습니다. 
<a href="https://papago.naver.net/website?locale=ko&source=en&target=ko&url=https%3A%2F%2Fdeveloper.apple.com%2Fdesign%2Fhuman-interface-guidelines%2Fios%2Fextensions%2Fsharing-and-actions" target="_blank"><b>Sharing and Actions</b></a>

<div class="gallery-box">
  <div class="gallery">
    <img src="/images/post/activity view/act1.png" alt="Project">
    <img src="/images/post/activity view/share1.png" width="337" alt="Project">
  </div>
</div>
<br/>

## Guideline
- <b>커스텀 activity를 표시하는 간단한 템플릿 이미지를 디자인해야 합니다.</b> <br/>
템플릿 이미지는 마스크를 사용하여 아이콘을 만들고, 적절한 투명도와 안티 앨리어싱이 가능하도록 블랙과 화이트를 사용하며, 드롭섀도우를 적용하면 안됩니다. 템플릿 이미지는 약 70px ✕ 70px 크기의 영역에 중심이 맞춰져야 합니다.
- <b>간단한 activity 제목을 만들어야 합니다.</b> <br/>
제목은 아이콘 아래 나타나고 짧은 제목이 좋습니다. 제목이 너무 길면 iOS는 먼저 텍스트를 축소하고 그 이상이면 생략합니다. 또한, 제목에 회사이름이나, 제품이름이 있으면 안됩니다.
- <b>Activity가 현재 상황에 적합한지 확인해야합니다.</b> <br/>
기본적으로 제공하는 avtivity는 순서를 변경할 수 없지만, 앱에 해당되지 않을 경우 제외할 수 있습니다. 또한, 지정된 시간에 표시할 activity를 구분할 수 있습니다.
- <b>버튼을 사용하여 activity view를 표시해야 합니다.</b> <br/>
사용자들은 시스템이 제공하는 activity에 엑세스하는 데 익숙해서 같은 기능인 것을 다른 방법으로 제공하면 안됩니다.

***

## UIActivityViewController

#### Acitivity Item
UIActivityViewController 클래스를 이용해 아래 아이템을 공유할 수 있습니다.

* 문자열(String)
* URL 링크(String)
* 이미지(UIImage)
* UIActivityItemSource 프로토콜을 따르는 커스텀 타입의 인스턴스
<br/>

#### Activity Type
UIActivityViewController 클래스가 기본적으로 제공하는 내보내기 서비스의 UIActivity에는 아래와 같은 종류가 있습니다.

```swift
// 읽기 목록에 추가
static let addToReadingList: UIActivityType

// 에어드롭으로 공유하기
static let airDrop: UIActivityType

// 연락처에 지정
static let assignToContact: UIActivityType

// Paste Board에 복사
static let copyToPasteboard: UIActivityType

// 메일 보내기
static let mail: UIActivityType

// 메시지 보내기
static let message: UIActivityType

// iBooks에서 열기
static let openInIBooks: UIActivityType

// 페이스북에 공유하기
static let postToFacebook: UIActivityType

// Flickr에 공유하기
static let postToFlickr: UIActivityType

// Tencent Weibo에 공유하기
static let postToTencentWeibo: UIActivityType

// 트위터에 공유하기
static let postToTwitter: UIActivityType

// Vimeo에 공유하기
static let postToVimeo: UIActivityType

// SinaWeibo에 공유하기
static let postToWeibo: UIActivityType

// 프린트
static let print: UIActivityType

// 카메라 롤에 저장하기
static let saveToCameraRoll: UIActivityType

// PDF 생성(iOS 11 부터 사용가능)
static let markupAsPDF: UIActivityType
```
<br/>

#### 메서드 및 프로퍼티
```swift
// 초기화 메서드로, UIActivityViewController 객체를 반환합니다.
init(activityItems: [Any], applicationActivities: [UIActivity]?)
// activityItems: [Any] 공유하려는 아이템으로 UIActivityItemSource 프로토콜을 준수하는 객체를 배열 형태로 넣어줄 수 있습니다.
// applicationActivities: [UIActivity]? 애플리케이션이 지원하는 커스텀 서비스를 나타내는 UIActivity 객체의 배열로, nil 값이 될 수 있습니다.

// 컨트롤러를 닫은 후 실행할 완료 핸들러입니다.
var completionWithItemsHandler: UIActivityViewControllerCompletionWithItemsHandler?

// UIActivityType 중 사용하지 않을 서비스를 지정합니다.
var excludedActivityTypes: [UIActivityType]?
```

<br/>

***