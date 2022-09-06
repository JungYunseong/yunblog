---
layout: post
title:  Image views
date:   2022-09-06 00:00:00 +0300
image:  '/images/post/imageViews/thumbnail.png'
tags:   [New_HIG]
---

> ##### <center>안녕하세요 정윤성입니다.<br> 새로운 Human Interface Guidelines를 스터디를 통해 공부하며 정리하는 중입니다.</center>
> <cite>✏️ 스터디원: <a href="https://velog.io/@lawn/series/NEW-HIG-2022" target="_blank">@Lawn</a> | <a href="https://velog.io/@andana/series/Lets-Study-HIG" target="_blank">@Dana</a> | <a href="https://velog.io/@halogen/Apple-HIG-Foundation-Layout" target="_blank">@Halogen</a> | <a href="" target="_blank">@Choi</a></cite>

***

# Image views
Image view는 투명하거나 불투명한 배경에 단일 이미지(때에 따라서는 애니메이션 이미지 시퀀스)를 표시합니다. Image view 내에서 이미지를 확대, 축소, 크기조정 또는 특정 위치에 고정할 수 있고 일반적으로는 상호작용 요소가 없습니다.
<br><br>

## Best Practices
<b>주목적이 단순히 이미지 표시인 경우 image view를 사용합니다.</b> 때에 따라 가끔 이미지를 인터랙티브하게 하고 싶을 때는, image view에 동작을 추가하는 대신 시스템에서 제공하는 <a href="/blog/button">버튼</a>을 사용해 이미지를 표시하는 방법을 고려해보세요. 

<b>인터페이스에 아이콘을 표시하려면 image view 대신 기호 또는 인터페이스 아이콘을 사용하는 것이 좋습니다.</b> <a href="/blog/sf-symbols">SF Symbols</a>는 개발자가 다양한 색상과 선명도로 사용할 수 있도록 간편한 벡터 기반의 이미지 라이브러리를 제공합니다. 글리프 또는 템플릿 이미지라고도 하는 <a href="/blog/icons">인터페이스 아이콘</a>은 일반적으로 투명하지 않은 픽셀이 색상을 수신할 수 있는 비트맵 이미지입니다. 기호와 인터페이스 아이콘 모두 개발자가 선택한 강조 색상(accent color)을 사용할 수 있습니다.
<br><br>

***

## Content
Image view에는 PNG, JPEG 및 PDF와 같은 다양한 형식의 이미지 데이터가 포함될 수 있습니다. 자세한 내용은 <a href="/blog/images">Image</a>를 확인해주세요.

<b>이미지에 위에 텍스트를 사용할 때 주의하세요.</b> 이미지 위에 텍스트를 사용하면 이미지가 잘 보이지 않을뿐더러 텍스트의 가독성을 모두 저하할 수 있습니다. 더 좋은 결과물을 위해 텍스트가 이미지와 잘 대비 되는지 확인하고 텍스트 그림자 또는 배경 레이어를 추가하는 것처럼 텍스트 개체를 두드러지게 하는 방법을 고려하세요.

<b>애니메이션 시퀀스의 모든 이미지에 일정한 크기를 사용하세요.</b> 뷰에 맞게 이미지의 크기를 사전 설정하면 시스템에서 크기를 조정할 필요가 없습니다. 시스템에서 이미지의 크기를 조정해야 하는 경우에 이미지의 크기와 모양을 맞추면 더 좋은 결과를 확인할 수 있습니다.

***
## Platform considerations
<c style="color: Gray">iOS 또는 iPadOS에 대한 추가 고려사항은 없습니다.</c>
<br>

### macOS
<b>앱에 편집할 수 있는 image view가 필요한 경우 image well을 사용하세요.</b> <a href="/blog/image-wells">Image well</a>은 복사, 붙여넣기, 끌기 및 삭제 키를 사용하여 내용을 지울 수 있는 image view입니다.

<b>클릭할 수 있는 이미지를 만들려면 image view대신 image button을 사용하세요.</b> <a href="/blog/image-buttons">image button</a>은 이미지 또는 아이콘을 포함하고 뷰에 나타나며 즉각적인 앱 관련 작업을 시작합니다.

### tvOS
많은 TVOS 이미지는 투명도를 가진 여러 레이어가 합쳐져 있어 깊이감을 줍니다. 자세한 내용은 <a href="/blog/images/#Layered-images">Layered Images</a>를 확인해주세요.

### watchOS
<b>가능할 경우 SwiftUI를 사용하여 애니메이션을 만드세요.</b> 필요한 경우 WatchKit을 사용하여 이미지 요소 내에서 이미지 시퀀스를 애니메이션화 할 수 있습니다. 개발자 가이던스는 <a href="https://developer.apple.com/documentation/watchkit/wkimageanimatable"></a>를 확인해주세요.

***
## Resources
#### Related
<a href="https://developer.apple.com/design/human-interface-guidelines/foundations/images">Images</a><br>
<a href="https://developer.apple.com/design/human-interface-guidelines/components/selection-and-input/image-wells">Image wells</a><br>
<a href="https://developer.apple.com/design/human-interface-guidelines/components/menus-and-actions/buttons/#image-buttons">Image buttons</a><br>
<a href="https://developer.apple.com/design/human-interface-guidelines/foundations/sf-symbols">SF Symbols</a><br>

#### Developer documentation
<a href="https://developer.apple.com/documentation/swiftui/image">Image - SwiftUI</a><br>
<a href="https://developer.apple.com/documentation/uikit/uiimageview">UIImageView - UIKit</a><br>
<a href="https://developer.apple.com/documentation/appkit/nsimageview">NSImageView - AppKit</a><br>
<a href="https://developer.apple.com/documentation/watchkit/wkinterfaceimage">WKInterfaceImage - WatchKit</a><br>

#### Videos
<div class="gallery-box">
  <div class="video-gallery">
    <a id="wwdc2021-10021" href="https://developer.apple.com/videos/play/wwdc2021/10021/">
		<img src="https://devimages-cdn.apple.com/wwdc-services/images/119/4887/4887_wide_250x141_2x.jpg" width="250" height="141"><br>
		<b>Add rich graphics to your<br>SwiftUI app</b><br>
		WWDC21
	</a>
    <a id="wwdc2020-10175" href="https://developer.apple.com/videos/play/wwdc2020/10175/">
		<img src="https://devimages-cdn.apple.com/wwdc-services/images/49/3823/3823_wide_250x141_2x.jpg" width="250" height="141"><br>
		<b>The details of UI<br>typography</b><br>
		WWDC 2020
	</a>
  </div>
</div>