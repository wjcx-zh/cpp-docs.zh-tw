---
title: "nullptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "nullptr_cpp"
  - "nullptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nullptr 關鍵字 [C++]"
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# nullptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定類型為 `std::nullptr_t` 的 Null 指標常數，此指標常數可以轉換成任何原始指標類型。雖然您可使用關鍵字 `nullptr` 而不含任何標頭，但如果您的程式碼使用類型 `std::nullptr_t`，則必須透過包含標頭 `<cstddef>` 來加以定義。  
  
> [!NOTE]
>  C\+\+\/CLI 也會針對 Managed 程式碼應用程式定義 `nullptr` 關鍵字，並且不可與 ISO 標準 C\+\+ 關鍵字互換。  如果您可能會使用以 Managed 程式碼為主的 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項編譯程式碼，則在任何一行您必須保證編譯器會使用原生 C\+\+ 解譯的程式碼中，使用 `__nullptr`。  如需詳細資訊，請參閱 [nullptr](../windows/nullptr-cpp-component-extensions.md)。  
  
## 備註  
 避免使用 `NULL` 或零 \(`0`\) 做為 Null 指標常數；`nullptr` 比較不容易誤用，而且在大多數情況下可以發揮比較好的效果。例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。巨集 NULL 會展開為 `0`，因此呼叫 `std::make_pair(0, 3.14)` 會傳回 `std::pair<int, double>` \(不可轉換為 func\(\) 的 `std::pair<const char *, double>` 參數類型\)。呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` \(可轉換為 `std::pair<const char *, double>`\)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)