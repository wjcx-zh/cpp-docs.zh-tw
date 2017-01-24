---
title: "Win32 Predefined Symbols | Microsoft Docs"
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
  - "Win32 [C++], predefined symbols"
  - "symbols, Win32 predefined"
  - "Windows API [C++], predefined symbols"
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Win32 Predefined Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些符號定義於 Win32 標頭檔中，但是它們可以支援標準的 Windows 應用程式函式與其動作。  這些符號主要用於通用的 UI 項目。  當您在資源編輯器中使用控制項時，這些符號會出現在與通用控制項相關聯的[屬性視窗](../Topic/Properties%20Window.md)中。  例如，若您的工具列應顯示應用程式圖示，該圖示將與 \[屬性\] 視窗中的符號 IDI\_SMALL 相關聯。  
  
|||  
|-|-|  
|IDABORT|控制項：對話方塊的 \[中止\] 按鈕|  
|IDC\_STATIC|控制項：對話方塊中的靜態文字|  
|IDCANCEL|控制項：對話方塊的 \[取消\] 按鈕|  
|IDD\_ABOUTBOX|對話方塊：\[關於產品\] 對話方塊|  
|IDI\_PROJECTNAME|圖示：目前的專案圖示|  
|IDI\_SMALL|圖示：目前的專案小圖示|  
|IDIGNORE|控制項：配合對話方塊上的 \[忽略\] 按鈕使用|  
|IDM\_ABOUT|功能表項目：配合 \[說明...\] 的 \[關於...\] 使用|  
|IDM\_EXIT|功能表項目：配合 \[檔案...\] 的 \[結束...\] 使用|  
|IDNO|控制項：對話方塊的 \[否\] 按鈕|  
|IDOK|控制項：對話方塊的 \[確定\] 按鈕|  
|IDRETRY|控制項：對話方塊的 \[重試\] 按鈕|  
|IDS\_APP\_TITLE|字串：目前的應用程式名稱|  
|IDYES|控制項：對話方塊的 \[是\] 按鈕|  
  
## 需求  
 Win32  
  
## 請參閱  
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)