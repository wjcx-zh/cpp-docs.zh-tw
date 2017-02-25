---
title: "搭配使用對話方塊列與 Rebar 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WM_EX_TRANSPARENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "對話方塊列, 與 Rebar 群組列一起使用"
  - "Rebar 控制項, 對話方塊列"
  - "WS_EX_TRANSPARENT 樣式"
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 搭配使用對話方塊列與 Rebar 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如 [Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)所述，每個群組列只能包含子視窗 \(或控制項\)。  如果您要有一個以上每個群組列，建立子視窗這可能是限制。  方便的解決方法是建立具有多個控制項的對話方塊列資源後加入 Rebar 群組列 \(包含對話方塊列\) 到 Rebar 控制項。  
  
 通常，因此，如果您要對話方塊列群組列顯示為透明，您會設定對話方塊列物件的 **WS\_EX\_TRANSPARENT** 延伸樣式。  不過，，因為 **WS\_EX\_TRANSPARENT** 具有適當繪製對話方塊列背景的問題，您必須完成這個額外的達到此效果。  
  
 下列程序說明的必要步驟達成透明度，而不使用 **WS\_EX\_TRANSPARENT** 延伸樣式。  
  
### 若要實作 Rebar 的透明對話方塊列中關聯  
  
1.  使用 [加入類別對話方塊](../mfc/reference/adding-an-mfc-class.md)，請將該新類別 \(例如， `CMyDlgBar`\) 實作自己的對話方塊列的物件。  
  
2.  將 `WM_ERASEBKGND` 訊息的處理常式。  
  
3.  在新的處理常式，請修改現有的程式碼符合下列範例:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  將 `WM_MOVE` 訊息的處理常式。  
  
5.  在新的處理常式，請修改現有的程式碼符合下列範例:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 新的處理常式會轉送 `WM_ERASEBKGND` 訊息到父視窗和強制重繪模擬對話方塊列的透明度，對話方塊列物件移動時。  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)