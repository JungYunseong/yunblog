---
layout: post
title:  Action Sheets
date:   2022-05-22 12:00:00 +0300
image:  '/images/post/actionSheets/action-sheets.jpg'
tags:   [SwiftUI, HIG, Development]
---
> An action sheet presents two or more choices related to an intentional user action.
>
> <cite><a href="https://papago.naver.net/website?locale=ko&source=en&target=ko&url=https%3A%2F%2Fdeveloper.apple.com%2Fdesign%2Fhuman-interface-guidelines%2Fios%2Fviews%2Faction-sheets%2F" target="_blank">Human Interface Guideline</a></cite>

계획적인 사용자 action과 관련된 두개 이상의 선택사항을 제시합니다. 

<center><img src="/images/post/actionSheets/action-sheets.png" width="300" alt="Project"></center> <br/>

iPhone과 같은 작은 화면에서는 action sheets를 사용하지만 iPad와 같은 큰 화면에서는 action sheet가 Popover 형태로 나타납니다.

<div class="gallery-box">
  <div class="gallery">
    <img src="/images/post/actionSheets/action-sheets.png" alt="Project">
    <img src="/images/post/actionSheets/ipad.png" width="434" alt="Project">
  </div>
</div>
<br/>

## Guideline
- <b>메뉴 방식이 아닌 action sheet를 사용하여 사용자가 시작한 action과 관련된 선택사항을 제공해야 합니다.</b> <br/>
예를 들어 사용자가 메일을 작성하다가 'cancel' 버튼을 눌렀다고 가정하면, 사용자는 '저장', '삭제', '취소'와 같은 action을 취할 수 있습니다. 현재 작업과 관련있는 작업일 때 action sheet를 사용하게 됩니다. 밀접한 관련이 없는 항목을 제공해야하는 경우 <a href="/blog/context-menu"><b>'context menu'</b></a>를 사용합니다.
- <b>사용자가 데이터를 삭제할 수 있는 작업을 거부할 수 있는 취소 버튼을 제공해야 합니다.</b> <br/>
Cancel(취소) 버튼을 action sheet 하단에 배치 합니다.
- <b>파괴적인 선택항목을 시각적으로 두드러지게 합니다.</b> <br/>
데이터를 삭제하는 것과 같은 파괴적인 action을 하는 항목을 사용할 경우 시각적으로 두드러지는 디자인을 사용하고(red 색상 사용 등) 이러한 항목을 action sheet 상단에 배치하여야 합니다.
- <b>action sheet가 스크롤 되지 않게 해야 합니다.</b> <br/>
action sheet의 버튼이 많을수록, 사용자들은 action을 선택하는데 많은 시간과 노력이 필요하게 됩니다. 그리고 action sheet는 버튼으로 이루어진 sheet이기 때문에 사용자가 스크롤을 하다 실수로 버튼을 누르는 경우가 있기 때문에 스크롤이 되지 않게 해야 합니다.

***

## SwiftUI에서 구현해보기

먼저, action Sheet를 표시할지 여부를 추적하는 속성을 정의해야 합니다. 그런 다음 action Sheet() 수정자를 사용하여 해당 속성을 모니터링하고 조건이 true가 되면 action Sheet를 표시하는 방식입니다.
```swift
struct modalActionSheets: View {
    
    @State var showActionSheet: Bool = false
    
    var body: some View {
        ZStack {
            Color.brown
                .edgesIgnoringSafeArea(.all)
            
            VStack {
                Button(action: {
                    showActionSheet.toggle()
                }) {
                    Text("Action Sheets")
                        .font(.title)
                        .foregroundColor(.white)
                }
            }
            // buttons: [.default(Text("")), .cancel(Text(""))]를 사용하여 일반 버튼과 취소 버튼을 설정합니다.
            .actionSheet(isPresented: $showActionSheet) {
                ActionSheet(title: Text("제목"),
                            message: Text("메시지"),
                            buttons: [.default(Text("One")), .default(Text("Two")), .cancel(Text("취소"))])
            }
        }
    }
}
```
<br/>
<center><img src="/images/post/actionSheets/actionSheet1.gif" width="300" height="500" alt="Project"></center>
<br/>
위와 같이, body에 actionSheet를 직접 만들어 사용할 수 있지만 여러개의 매개변수로 인해 코드가 길어지게 되면 지져분해 보입니다. <br/>
이때 <a href="/blog/function"><b>함수</b></a>를 사용하여 코드를 정리할 수 있습니다.

```swift
struct modalActionSheets2: View {
    
    @State var showActionSheet: Bool = false
    
    var body: some View {
        ZStack {
            Color.brown
                .edgesIgnoringSafeArea(.all)
            
            VStack {
                Button(action: {
                    showActionSheet.toggle()
                }) {
                    Text("Action Sheets")
                        .font(.title)
                        .foregroundColor(.white)
                }
            }
            .actionSheet(isPresented: $showActionSheet, content: myActionSheet)
        }
    }
}

func myActionSheet() -> ActionSheet {
    let button1: ActionSheet.Button = .default(Text("One"))
    let button2: ActionSheet.Button = .default(Text("Two"))
    let button3: ActionSheet.Button = .cancel(Text("취소"))
    
    let title = Text("제목")
    let message = Text("메시지")
    
    return ActionSheet(title: title,
                       message: message,
                       buttons: [button1, button2, button3]
    )
}
```

***