---
title: "ATL Predefined Symbols | Microsoft Docs"
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
  - "symbols, ATL predefined"
  - "ATL symbols"
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Predefined Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些符號都定義於 ATL 標頭檔中，但是它們可以支援標準的 Windows 應用程式函式與其動作。  這些符號主要用於對話方塊。  當您在[對話方塊編輯器](../mfc/dialog-editor.md)中使用對話方塊和控制項時，這些符號會出現在與通用控制項相關聯的 \[屬性\] 視窗中。  例如，若您的對話方塊有一個 \[取消\] 按鈕，該命令將與[屬性視窗](../Topic/Properties%20Window.md)中的符號 IDCANCEL 相關聯。  
  
|||  
|-|-|  
|IDABORT|控制項：對話方塊的 \[中止\] 按鈕|  
|IDC\_STATIC|控制項：靜態控制項|  
|IDCANCEL|控制項：對話方塊的 \[取消\] 按鈕|  
|IDIGNORE|控制項：對話方塊的 \[忽略\] 按鈕|  
|IDNO|控制項：對話方塊的 \[否\] 按鈕|  
|IDOK|控制項：對話方塊的 \[確定\] 按鈕|  
|IDR\_ACCELERATOR1|資源：快速鍵對應表|  
|IDRETRY|控制項：對話方塊的 \[重試\] 按鈕|  
|IDS\_PROJNAME|字串：目前的應用程式名稱|  
|IDYES|控制項：對話方塊的 \[是\] 按鈕|  
  
## 需求  
 ATL  
  
## 請參閱  
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)