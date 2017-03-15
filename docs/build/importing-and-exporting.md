---
title: "匯入和匯出 | Microsoft Docs"
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
  - "__declspec(dllimport) 關鍵字 [C++]"
  - "DLL [C++], 匯出自"
  - "DLL [C++], 匯入"
  - "匯出 DLL [C++]"
  - "匯入 DLL [C++]"
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 匯入和匯出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用兩個方法，將公用符號匯入至應用程式或從 DLL 匯出函式：  
  
-   在建置 DLL 時使用模組定義 \(.def\) 檔  
  
-   在主應用程式的函式定義中使用 **\_\_declspec\(dllimport\)** 或 **\_\_declspec\(dllexport\)** 關鍵字  
  
## 使用 .def 檔  
 模組定義 \(.def\) 檔是文字檔，包含一或多個模組陳述式，說明 DLL 的各種屬性 \(Attribute\)。  如果您不使用 **\_\_declspec\(dllimport\)** 或 **\_\_declspec\(dllexport\)** 來匯出 DLL 的函式，DLL 就需要使用 .def 檔。  
  
 您可以使用 .def 檔[匯入至應用程式](../build/importing-using-def-files.md)或[從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)。  
  
## 使用 \_\_declspec  
 Visual C\+\+ 使用 **\_\_declspec\(dllimport\)** 和 **\_\_declspec\(dllexport\)** 來取代先前用於 16 位元版 Visual C\+\+ 的 **\_\_export** 關鍵字。  
  
 您並不需要用 **\_\_declspec\(dllimport\)** 來正確編譯程式碼，但是如果使用了可以讓編譯器產生更佳的程式碼。  編譯器可以產生較佳的程式碼，因為它能判斷函式是否存在於 DLL 中，這可以讓編譯器產生略過一層間接取值 \(Indirection，通常出現在跨越 DLL 邊界的函式呼叫\) 的程式碼。  不過您必須使用 **\_\_declspec\(dllimport\)**，匯入在 DLL 中使用的變數。  
  
 有了適當的 .def 檔 EXPORTS 區段，就不需要 **\_\_declspec\(dllexport\)**。  **\_\_declspec\(dllexport\)** 的加入，是為了提供簡便的方式，從 .exe 或 .dll 檔匯出函式而不使用 .def 檔。  
  
 Win32 的可攜執行格式 \(Portable Executable Format\) 是設計成將匯入會影響到的頁數降到最低。  為了達到這個目的，它將任何程式的所有匯入位址置於一個位置，稱為匯入位址表 \(Import Address Table\)。  如此可讓載入器在存取這些匯入時，只需要變更一頁或兩頁即可。  
  
## 您想要執行甚麼工作？  
  
-   [匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)