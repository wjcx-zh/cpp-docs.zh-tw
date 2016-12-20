---
title: "標準 Windows 訊息的處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afx_msg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式 [C++], 處理常式"
  - "處理函式, 標準 Windows 訊息"
  - "訊息處理 [C++], Windows 訊息處理常式"
  - "訊息 [C++], Windows"
  - "Windows 訊息 [C++], 處理常式"
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標準 Windows 訊息的處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標準 Windows 訊息 \(**WM\_**\) 預設處理常式在類別 `CWnd`預先定義。  類別庫根據這些處理常式訊息名稱為基礎。  例如， `WM_PAINT` 訊息的處理常式在 `CWnd` 宣告如下:  
  
 `afx_msg void OnPaint();`  
  
 **afx\_msg** 關鍵字傳遞差異處常式建議 C\+\+ **virtual** 關鍵字的作用與其他 `CWnd` 成員函式。  不過，請注意，這些函式實際上並不是真正的;它們只會將訊息對應中實作。  訊息對應取決於標準前置處理器巨集，而不是 C\+\+ 語言所有擴充功能。  **afx\_msg** 關鍵字解析為在前置處理之後空白字元。  
  
 若要覆寫基底類別中定義的處理常式，請定義與相同的原型函式在您的衍生類別和執行處理常式的訊息對應項目。  您的處理常式「覆寫」相同名稱的所有處理常式中的任何您類別的基底類別。  
  
 在某些情況下，處理常式應該呼叫基底類別的覆寫的處理常式，因此基底類別和視窗可以處理訊息。  如果您呼叫您的覆寫的基底類別處理常式決定條件。  有時您必須首先呼叫基底類別處理常式，有時最後。  在某些情況下，如果您選擇不要處理訊息，有條件地呼叫基底類別處理常式。  有時候您應該呼叫基底類別處理常式，然後有條件地根據基底類別處理常式或狀態執行您的處理常式程式碼，並傳回此值。  
  
> [!CAUTION]
>  如果您想要將它們傳遞給基底類別處理常式，修改引數傳遞至處理常式並不安全。  例如，您可能會誘想要修改 `OnChar` 處理常式的 `nChar` 引數 \(例如轉換為大寫\)。  此行為相當陰影暗的，但是如果您需要完成此效果，請使用 `CWnd` 成員函式 **SendMessage** 。  
  
 如何判斷適當的方式覆寫已指定訊息?  在屬性視窗中針對指定的訊息時— `WM_CREATE`的 `OnCreate` 處理常式所寫入處理函式的基本架構，例如以建議的覆寫成員函式的形式，它會寫入。  下列範例建議處理常式會先呼叫基底類別處理常式並執行，只有在不傳回 \-1 前提下。  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/CPP/handlers-for-standard-windows-messages_1.cpp)]  
  
 依照慣例，這些處理常式名稱是以 "On" 開始。而其他取得陣列，其中一些處理常式不接受引數。  除了 `void`以外，也有一些傳回型別。  所有 **WM\_** 訊息的預設處理常式 *MFC 參考* 文件名稱從「啟動類別 `CWnd` 的成員函式」。在 `CWnd` 的成員函式宣告的前面加上 **afx\_msg**。  
  
## 請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)