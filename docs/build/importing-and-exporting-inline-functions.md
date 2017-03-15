---
title: "匯入和匯出內嵌函式 | Microsoft Docs"
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
  - "DLL [C++], 匯出自"
  - "DLL [C++], 匯入"
  - "匯出函式 [C++], 內嵌函式"
  - "函式 [C++], 匯出"
  - "函式 [C++], 匯入"
  - "匯入函式 [C++]"
  - "匯入內嵌函式 [C++]"
  - "內嵌函式 [C++], 匯出"
  - "內嵌函式 [C++], 匯入"
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 匯入和匯出內嵌函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

匯入函式可以定義成內嵌 \(Inline\)。  此作用大致上與定義標準函式內嵌相同；對函式的呼叫會展開成內嵌程式碼，這點與巨集非常相似。  這種方式對於支援 DLL 中基於效能考量而內嵌某些成員函式的 C\+\+ 類別 \(Class\) 很有用。  
  
 匯入內嵌函式的其中一個功能是，您可以在 C\+\+ 裡取得它的位址。  編譯器傳回常駐在 DLL 裡內嵌函式複本的位址。  匯入內嵌函式的另一項功能是，您可以初始化匯入函式的靜態區域資料，這點與全域匯入資料不同。  
  
> [!CAUTION]
>  在提供匯入的內嵌函式時請務必小心，因為它們可能會導致版本衝突。  內嵌函式會展開至應用程式碼；因此，如果稍後您重寫函式，除非應用程式本身重新編譯，否則並不會將其更新 \(通常，可以在無須重建使用它們的應用程式之下更新 DLL 函式\)。  
  
## 您想要執行甚麼工作？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## 請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)