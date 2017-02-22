---
title: "FreeLibrary 和 AfxFreeLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FreeLibrary"
  - "AfxFreeLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "擴充 DLL [C++]，卸載"
  - "AfxFreeLibrary 方法"
  - "卸載 DLL"
  - "FreeLibrary 方法"
  - "DLL [C++]，連結"
  - "明確連結 [C++]"
  - "DLL [C++]，卸載"
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# FreeLibrary 和 AfxFreeLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當不再需要 DLL 模組時，明確連結至 DLL 的處理序會呼叫 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) 函式。  這個函式會遞減模組的參考次數，並在參考到的次數為零的時候，解除它在處理序的位址空間的對應。  
  
 在 MFC 應用程式中，應該使用 [AfxFreeLibrary](../Topic/AfxFreeLibrary.md)，而不是 `FreeLibrary` 來卸載擴充 DLL。  `AfxFreeLibrary` 的介面 \(函式原型\) 與 `FreeLibrary` 相同。  
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../Topic/AfxFreeLibrary.md)