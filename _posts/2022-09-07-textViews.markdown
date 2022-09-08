---
layout: post
title:  Text views
date:   2022-09-07 00:00:00 +0300
image:  '/images/post/textViews/thumbnail.png'
tags:   [New_HIG]
---

> ##### <center>안녕하세요 정윤성입니다.<br> 새로운 Human Interface Guidelines를 스터디를 통해 공부하며 정리하는 중입니다.</center>
> <cite>✏️ 스터디원: <a href="https://velog.io/@lawn/series/NEW-HIG-2022" target="_blank">@Lawn</a> | <a href="https://velog.io/@andana/series/Lets-Study-HIG" target="_blank">@Dana</a> | <a href="https://velog.io/@halogen/Apple-HIG-Foundation-Layout" target="_blank">@Halogen</a> | <a href="" target="_blank">@Choi</a></cite>

***

# Text views
Text view는 선택적으로 편집할 수 있는 여러 줄의 스타일 텍스트 내용을 표시합니다.<br><br>
Text views는 임의의 높이 일 수 있으며 내용이 뷰 외부로 확장될 때 스크롤을 사용할 수 있습니다. 기본적으로 text view의 내용은 왼쪽 정렬되며 시스템 레이블 색상을 사용합니다. iOS 또는 iPadOS에서 text view를 편집할 수 있는 경우 뷰를 선택할 때 키보드가 나타납니다.
<br><br>

## Best Practices
**편집할 수 있거나 특수한 형식으로 텍스트를 표시해야 할 경우 text view를 사용하세요.** Text view는 특수 텍스트를 표시하고 텍스트 입력을 수신하는 데 가장 많은 옵션을 제공한다는 점에서 [text fields](https://papago.naver.net/apis/site/proxy?url=https%3A%2F%2Fdeveloper.apple.com%2Fdesign%2Fhuman-interface-guidelines%2Fcomponents%2Fselection-and-input%2Ftext-fields)와 [labels](https://papago.naver.net/apis/site/proxy?url=https%3A%2F%2Fdeveloper.apple.com%2Fdesign%2Fhuman-interface-guidelines%2Fcomponents%2Flayout-and-organization%2Flabels)과 다릅니다. 적은 양의 텍스트를 표시해야 하는 경우 레이블을 대신 사용하거나 텍스트를 편집해야 하는 경우에는 text field를 사용하는 것이 더 간단합니다.

**텍스트를 읽을 수 있도록 해야 합니다.** 여러 글꼴, 색상 및 정렬을 창의적으로 사용할 수 있지만 콘텐츠의 가독성을 유지하는 것이 중요합니다. Dynamic Type을 채택해서 디바이스의 텍스트 크기가 변경되더라도 텍스트가 계속 표시되게 하는 것이 좋습니다.
<c style="color: SteelBlue">Dynamic Type이란, 사용자가 원하는 글씨 사이즈로 App contents를 볼 수 있는 적응성(flexibility)을 제공합니다.</c>
<center><img src="/images/post/textViews/textViews1.png" alt="Dynamic Type"></center><br>
 굵은 텍스트와 같이 accessibility 옵션도 사용 가능하도록 설정하여 콘텐츠를 테스트해야 합니다. 자세한 내용은 [Accessibility](https://developer.apple.com/design/human-interface-guidelines/foundations/accessibility)와 [Typograpy](https://developer.apple.com/design/human-interface-guidelines/foundations/typography)을 확인하세요.

 **유용한 텍스트를 선택할 수 있도록 합니다.** Text view에 오류메시지, 일련번호 또는 IP 주소와 같은 유용한 정보가 포함된 경우, 다른 곳에 붙여넣기 위해 사용자가 선택하고 복사할 수 있도록 하세요.

 ***

## Platform considerations
<c style="color: Gray">macOS에 대한 추가 고려사항은 없습니다.</c>
<br>

### iOS, iPadOS
**적절한 키보드 타입을 표시합니다.** 키보드 타입은 여러 가지가 있으며, 각각 다른 타입의 입력에 대응하도록 설계되어 있습니다. 데이터 입력을 간소화하려면 text view를 편집할 때 표시하는 키보드가 콘텐츠 유형에 적합해야 합니다. 자세한 내용은 [Onscreen keyboards](https://developer.apple.com/design/human-interface-guidelines/components/selection-and-input/onscreen-keyboards)을 확인해주세요.

### tvOS
Text view를 사용하여 tvOS에서 텍스트를 표시할 수 있습니다. tvOS의 텍스트 입력은 최소로 설계되었기 때문에 tvOS는 편집할 수 있는 텍스트 대신 [text fields](https://developer.apple.com/design/human-interface-guidelines/components/selection-and-input/text-fields)를 사용합니다.

### watchOS
WatchKit의 레이블 또는 SwiftUI의 text view로 watchOS에 텍스트를 표시할 수 있습니다. 자세한 내용은 [Labels](https://developer.apple.com/design/human-interface-guidelines/components/layout-and-organization/labels)를 확인하세요.

***

## Resources
#### Related
[Labels](https://developer.apple.com/design/human-interface-guidelines/components/layout-and-organization/labels)<br>
[Text fields](https://developer.apple.com/design/human-interface-guidelines/components/selection-and-input/text-fields)<br>
[Combo boxes](https://developer.apple.com/design/human-interface-guidelines/components/content/design/human-interface-guidelines/components/selection-and-input/combo-boxes)<br>

#### Developer documentation
[Text — SwiftUI](https://developer.apple.com/documentation/swiftui/text)<br>
[UITextView — UIKit](https://developer.apple.com/documentation/uikit/uitextview)<br>
[NSTextView — AppKit](https://developer.apple.com/documentation/appkit/nstextview)