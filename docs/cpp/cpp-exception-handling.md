---
title: "C++ 例外狀況處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理"
  - "Visual C++, 例外狀況處理"
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 例外狀況處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 語言內建擲回和攔截例外狀況支援。  使用 C\+\+ 設計程式時，您應盡可能使用本節所述的內建 C\+\+ 例外狀況支援。  
  
 若要在程式碼中啟用 C\+\+ 例外狀況處理，請使用 [\/EHsc](../build/reference/eh-exception-handling-model.md)。  
  
## 本章節內容  
 以下關於 C\+\+ 例外狀況處理的討論包括：  
  
-   [try、catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [評估 Catch 區塊的方式](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [例外狀況和堆疊回溯](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [例外狀況規格](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [未處理的 C\+\+ 例外狀況](../cpp/unhandled-cpp-exceptions.md)  
  
-   [混合 C \(結構化\) 和 C\+\+ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## 對於舊版 MFC 例外狀況的支援  
 從 4.0 版開始，MFC 開始使用 C\+\+ 例外狀況處理機制。  雖然建議您在新的程式碼中使用 C\+\+ 例外狀況處理，但 MFC 4.0 \(含\) 以後版本會保留舊版的 MFC 巨集，因此舊程式碼不會出現錯誤。  並且，您可以合併巨集和新的機制。  如需混合巨集和 C\+\+ 例外狀況處理的資訊，以及轉換舊程式碼以使用新的機制的資訊，請參閱下列文章：[例外狀況：使用 MFC 巨集和 C\+\+ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)及[例外狀況：從 MFC 例外狀況巨集進行轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  如果您仍然使用舊版的 MFC 例外狀況巨集，它們會判斷值為 C\+\+ 例外狀況關鍵字。  請參閱[例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。  
  
## 請參閱  
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)