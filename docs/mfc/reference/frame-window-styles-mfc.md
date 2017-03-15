---
title: "框架視窗樣式 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FWS_ADDTOTITLE"
  - "FWS_SNAPTOBARS"
  - "FWS_PREFIXTITLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架視窗, 樣式"
  - "FWS_ADDTOTITLE 常數"
  - "FWS_PREFIXTITLE 常數"
  - "FWS_SNAPTOBARS 常數"
  - "樣式, 視窗"
ms.assetid: d21f270e-a088-4962-a2ae-8c03334b5a06
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 框架視窗樣式 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **FWS\_ADDTOTITLE** 指定資訊附加至框架視窗標題的結尾。  例如， 「Microsoft 繪製\-在 Document1 繪製」。  您在應用程式精靈的文件樣板字串選項可以指定顯示的字串。  如果您需要關閉這個選項，覆寫 `CWnd::PreCreateWindow` 成員函式。  
  
-   **FWS\_PREFIXTITLE** 在應用程式名稱前顯示文件名稱在框架視窗標題。  例如， 「\-」WordPad 文件。  您在應用程式精靈的文件樣板字串選項可以指定顯示的字串。  如果您需要關閉這個選項，覆寫 `CWnd::PreCreateWindow` 成員函式。  
  
-   **FWS\_SNAPTOBARS** 封入一列控制項的控制項大小框架視窗，當它在浮動視窗而不是停駐到框架視窗。  這個樣式調整視窗以配合控制列。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)