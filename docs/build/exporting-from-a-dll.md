---
title: "從 DLL 匯出 | Microsoft Docs"
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
  - "DLL 匯出 [C++]"
  - "DLL [C++], 匯出自"
  - "匯出 DLL [C++]"
  - "匯出 DLL [C++], 關於自 DLL 匯出"
  - "匯出函式 [C++], DLL (匯出)"
  - "匯出表 [C++]"
  - "函式 [C++], 匯出"
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 從 DLL 匯出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DLL 檔具有和 .exe 檔非常相似的配置，但是有一個重大的差異：DLL 檔包含匯出表。  匯出表包含每個由 DLL 匯出到其他可執行檔的函式名稱。  這些函式是 DLL 的進入點；只有匯出表格裡的函式可由其他可執行檔存取。  DLL 裡的其他任何函式對 DLL 都是私用的。  可以使用具 \/EXPORTS 選項的 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具來檢視 DLL 的匯出表。  
  
 您可以使用兩種方法從 DLL 匯出函式：  
  
-   建立模組定義 \(.def\) 檔，並在建置 DLL 時使用 .def 檔。  如果您要[根據序數而不是名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)，請使用這個方法。  
  
-   在函式的定義裡使用關鍵字 **\_\_declspec\(dllexport\)**。  
  
 無論使用任何一種匯出函式方法，都要確定使用 [\_\_stdcall](../cpp/stdcall.md) 呼叫慣例。  
  
## 您想要執行甚麼工作？  
  
-   [使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [根據序數而不是名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入至應用程式](../build/importing-into-an-application.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## 請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)