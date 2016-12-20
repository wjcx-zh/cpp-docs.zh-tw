---
title: "裝置內容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BeginPaint 方法, CPaintDC"
  - "CClientDC 類別, 和 GetDC 方法"
  - "CClientDC 類別, 和 ReleaseDC 方法"
  - "CDC 類別, 物件"
  - "工作區"
  - "工作區, 和裝置內容"
  - "CMetaFileDC 類別, 和 OnPrepareDC 方法"
  - "CPaintDC 類別, 繪製的裝置內容"
  - "裝置內容 [C++]"
  - "裝置內容 [C++], 關於裝置內容"
  - "裝置內容 [C++], CDC 類別"
  - "裝置獨立繪圖"
  - "繪製, 裝置內容"
  - "繪製, 直接到視窗"
  - "繪製, 在滑鼠和裝置內容中"
  - "EndPaint 方法"
  - "框架視窗 [C++], 裝置內容"
  - "GDI 物件 [C++], 裝置內容"
  - "GetDC 方法和 CClientDC 類別"
  - "圖形物件, 裝置內容"
  - "中繼檔和裝置內容"
  - "滑鼠 [C++], 繪圖和裝置內容"
  - "OnPrepareDC 方法"
  - "繪製和裝置內容"
  - "印表機 [C++], 裝置內容"
  - "ReleaseDC 方法"
  - "使用者介面 [C++], 裝置內容"
  - "視窗 [C++], 和裝置內容"
  - "視窗 [C++], 直接繪圖到"
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 裝置內容
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

裝置內容是包含裝置的繪圖屬性視窗資料結構等資訊顯示或印表機。  所有繪製呼叫透過裝置內容物件呼叫，封裝繪製線條、形狀和文字的 Windows API。  裝置內容允許在視窗的與裝置無關的繪圖。  裝置內容可以用來繪製至畫面，印表機，或加入至中繼檔。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) 物件在裝置內容封裝，呼叫 `BeginPaint` 函式，然後繪製，然後呼叫 `EndPaint` 函式的視窗慣用語。  `CPaintDC` 建構函式會呼叫，則為 `BeginPaint` ，且解構函式呼叫 `EndPaint`。  簡化的流程是建立 [CDC](../mfc/reference/cdc-class.md) 物件，繪製，然後終結 `CDC` 物件。  在架構中，即使這個處理序自動執行。  特別是，則 `OnDraw` 函式會傳遞 `CPaintDC` 已經準備 \(透過 `OnPrepareDC`\)，因此，您引入它。  這個框架終結，而且基礎裝置內容釋放至傳回的視窗將呼叫加入至 `OnDraw` 函式。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) 物件封裝與代表視窗的工作區的裝置內容一起使用。  `CClientDC` 建構函式會呼叫 `GetDC` 函式和解構函式呼叫 `ReleaseDC` 函式。  [CWindowDC](../mfc/reference/cwindowdc-class.md) 物件封裝表示整個視窗的裝置內容，包括它的框架。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) 物件封裝繪圖到 Windows 中繼檔。  使用 `CPaintDC` 傳遞給 `OnDraw`，您必須在這個案例中呼叫 [OnPrepareDC](../Topic/CView::OnPrepareDC.md) 。  
  
## 滑鼠繪圖  
 在架構計劃進行繪製 \(因此大部分裝置內容工作—在檢視的 `OnDraw` 成員函式。  不過，您可以在其他用途仍然使用裝置內容物件。  例如，在檢視的上方時提供追蹤意見，您需要引入直接檢視，而不用等候 `OnDraw` 呼叫。  
  
 在這種情況下，您可以使用 [CClientDC](../mfc/reference/cclientdc-class.md) 裝置內容物件引入直接檢視。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="a12b51e88715aef1e34dc9b8f4447117" class\="tgtSentence"\>裝置內容 \(定義\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [繪製在檢視](../mfc/drawing-in-a-view.md)  
  
-   [您可以檢視輸入的解譯使用者](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f3dbb554cb14503827bf0ebda53953d7" class\="tgtSentence"\>直線和曲線\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [\<caps:sentence id\="tgt26" sentenceid\="365f749101c5eabc8b3be48de1dc3d6b" class\="tgtSentence"\>填滿的形狀\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [\<caps:sentence id\="tgt27" sentenceid\="dc86a6302992c2d9f64d0fc6a8cfef75" class\="tgtSentence"\>字型和文字\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [\<caps:sentence id\="tgt28" sentenceid\="62848e3ce5804aa985513a7922ff87b2" class\="tgtSentence"\>Colors\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [\<caps:sentence id\="tgt29" sentenceid\="ee85800dfcba9a5bdf11f101e1bbadeb" class\="tgtSentence"\>座標空間和轉換\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)