---
title: "如何：使用訊息對應交互參考 | Microsoft Docs"
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
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "視窗 [C++], 訊息對應"
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用訊息對應交互參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在標記 \<memberFxn\> 的輸入，為衍生自 [CWnd](../../mfc/reference/cwnd-class.md) 的類別中撰寫自己的成員函式。  您可以使用的函式想要的任何名稱。  其他功能，例如 `OnActivate`， `CWnd`是類別的成員函式。  如果呼叫，就會將訊息傳遞至 `DefWindowProc` 的 Windows 函式。  若要處理 Windows 通知訊息，請覆寫在衍生類別中對應的 `CWnd` 函式。  您的函式應該中呼叫基底類別的覆寫函式讓基底類別和 Windows 回應訊息。  
  
 在所有情況下，請將函式原型在 `CWnd`衍生類別標頭，以及撰寫訊息對應項目如下所示。  
  
 使用下列詞彙:  
  
|詞彙|定義|  
|--------|--------|  
|id|任何使用者定義的功能表項目 ID \(**WM\_COMMAND** \) 訊息或控制項 ID \(子視窗通知訊息\)。|  
|「訊息」和「wNotifyCode」|在 WINDOWS.H 定義視窗訊息 ID 。|  
|nMessageVariable|包含從 **RegisterWindowMessage** Windows 函式的傳回值的變數名稱。|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)