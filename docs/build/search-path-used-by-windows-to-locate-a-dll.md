---
title: "Windows 用來找出 DLL 的搜尋路徑 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], Windows 搜尋路徑"
  - "尋找 DLL"
  - "已知的 DLL 搜尋 [C++]"
  - "找出 DLL"
  - "搜尋路徑 [C++]"
  - "搜尋 [C++], DLL"
  - "Windows [C++], DLL 搜尋路徑"
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 用來找出 DLL 的搜尋路徑
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用明確和隱含連結，Windows 首先會搜尋「已知的 DLL」，例如 Kernel32.dll 和 User32.dll。  接著 Windows 會依照下列順序搜尋 DLL：  
  
1.  目前處理序之可執行模組的所在目錄。  
  
2.  目前的目錄。  
  
3.  Windows 系統目錄。  **GetSystemDirectory** 函式擷取這個目錄的路徑。  
  
4.  Windows 目錄。  **GetWindowsDirectory** 函式擷取這個目錄的路徑。  
  
5.  列於 PATH 環境變數的目錄。  
  
    > [!NOTE]
    >  不會用到 LIBPATH 環境變數。  
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [明確連結](../build/linking-explicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)