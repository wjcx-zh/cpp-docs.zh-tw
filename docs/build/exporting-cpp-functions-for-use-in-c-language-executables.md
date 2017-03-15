---
title: "匯出 C++ 函式以用於 C 語言可執行檔 | Microsoft Docs"
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
  - "匯出 DLL [C++], C 可執行檔中的 C++ 函式"
  - "匯出函式 [C++], C 可執行檔中的 C++ 函式"
  - "函式 [C++], C 可執行檔中的 C++ 函式"
  - "函式 [C++], 匯出"
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 匯出 C++ 函式以用於 C 語言可執行檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您在 DLL 裡有用 C\+\+ 撰寫且希望從 C 語言模組裡存取的函式，您便應該使用 C 連結而不是 C\+\+ 連結來宣告這些函式。  除非有其他的指定，否則 C\+\+ 編譯器會使用 C\+\+ 型別安全命名 \(也稱為名稱裝飾 \(Name Decoration\)\) 和 C\+\+ 呼叫慣例，但是如此要從 C 呼叫就會比較困難。  
  
 若要指定 C 連結，請為您的函式宣告指定 **extern** "**C**"。  例如：  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## 您想要執行甚麼工作？  
  
-   [使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
-   [連結規格](http://msdn.microsoft.com/zh-tw/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)