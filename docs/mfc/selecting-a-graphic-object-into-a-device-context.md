---
title: "選取圖形物件放入裝置內容中 | Microsoft Docs"
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
  - "裝置內容, 圖形物件"
  - "裝置內容, 選取圖形物件放入"
  - "GDI 物件 [C++], 裝置內容"
  - "圖形物件, 選取放入裝置內容中"
  - "存留期, 圖形物件"
  - "SelectObject 方法"
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 選取圖形物件放入裝置內容中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題適用於使用圖形物件在視窗的裝置內容。  在 [建立繪圖物件](../mfc/one-stage-and-two-stage-construction-of-objects.md)，您必須選取到裝置內容中儲存的預設物件位置其中之後:  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/CPP/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## 存留期的圖形物件。  
 [SelectObject](../Topic/CDC::SelectObject.md) 傳回的圖表物件為暫存的」。也就是說，下次程式取得閒置時間，它會由類別刪除 `CWinApp` 的 [OnIdle](../Topic/CWinApp::OnIdle.md) 成員函式。  只要您在單一函式使用 `SelectObject` 所傳回的物件，而不會傳回控制項的主要訊息迴圈，就不會有問題。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
-   [圖形物件的階段和兩階段建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [裝置內容。](../mfc/device-contexts.md)  
  
-   [繪製在檢視](../mfc/drawing-in-a-view.md)  
  
## 請參閱  
 [圖形物件](../mfc/graphic-objects.md)