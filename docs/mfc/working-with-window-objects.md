---
title: "使用視窗物件 | Microsoft Docs"
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
  - "子視窗, 使用"
  - "視窗物件, 使用"
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用視窗物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

與視窗呼叫來要求兩種活動:  
  
-   處理 Windows 訊息。  
  
-   在 Windows  
  
 要處理的視窗訊息，包括您的子視窗，請參閱 [out 此函式之對應訊息](../mfc/reference/mapping-messages-to-functions.md) 將訊息加入至 C\+\+ Windows 類別。  然後將訊息處理常式成員函式在您的類別。  
  
 在架構應用程式中最常見的繪圖在檢視結果， [OnDraw](../Topic/CView::OnDraw.md) 成員函式，每當需要繪製視窗的內容。  如果您的視窗是檢視的子系，您可能委派特定檢視的繪製至子視窗會以 `OnDraw` 呼叫您的視窗的成員函式中。  
  
 無論如何，您將需要繪製的裝置內容。  您可以使用這個內建畫筆、筆刷和在裝置內容包含的其他圖形物件相關聯的視窗。  也可以修改這些物件取得所需的繪圖的效果。  在您的裝置內容會設定為您的需要，呼叫 [CDC](../mfc/reference/cdc-class.md) 類別 \(裝置內容類別\) 的成員函式繪製線條，圖案和文字;使用色彩;並與座標系統一起使用。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
-   [繪製在檢視](../mfc/drawing-in-a-view.md)  
  
-   [裝置內容。](../mfc/device-contexts.md)  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)