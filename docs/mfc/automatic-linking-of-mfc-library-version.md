---
title: "MFC 程式庫版本的自動連結 | Microsoft Docs"
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
  - "defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自動連結 [C++]"
  - "MFC 中的預設程式庫"
  - "連結 [C++]"
  - "連結 [C++], MFC 程式庫版本的自動"
  - "連結 [C++], MFC 的"
  - "MFC 程式庫, 連結至"
  - "MFC 程式庫, 版本"
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 程式庫版本的自動連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 版本在 3.0 版之前的 \(在 Visual C\+\+ 2.0 版\) 前，您在程式庫輸入清單必須手動指定 MFC 程式庫的正確版本的連結器。  MFC 3.0 版和更新版本中，手動指定的 MFC 程式庫版本不再是必要的。  相反的，MFC 標頭檔會根據`#define`定義的值，例如 **\_DEBUG** 或**\_UNICODE**，自動地決定正確 MFC 程式庫版本。  MFC 標頭檔會加入 **\/defaultlib**指示詞，指示連結器連結特定的 MFC 程式庫版本。  
  
 例如，下列程式碼片段從 AFX.H 標頭檔在 MFC NAFXCWD.LIB 或 NAFXCW.LIB 版本指示連結器連結，根據您使用的是 MFC 偵錯版本：  
  
 `#ifndef _UNICODE`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "nafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "nafxcw.lib")`  
  
 `#endif`  
  
 `#else`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "uafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "uafxcw.lib")`  
  
 `#endif`  
  
 `#endif`  
  
 MFC 標頭檔在所有必要程式庫中的連結，包括 MFC 程式庫、 Win32 程式庫、 OLE 程式庫、從範例建置的 OLE 程式庫、 ODBC 程式庫，依此類推。  Win32 程式庫包含 Kernel32.Lib、User32.Lib 和 GDI32.Lib。  
  
## 請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)