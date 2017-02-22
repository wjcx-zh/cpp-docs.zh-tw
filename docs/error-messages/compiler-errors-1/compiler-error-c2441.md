---
title: "編譯器錯誤 C2441 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2441"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2441"
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2441
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 以 \_\_declspec\(process\) 宣告的符號在 \/clr:pure 模式中必須是 const  
  
 變數在 **\/clr:pure** 之下是預設為應用程式定義域專屬。  如果在一個應用程式定義域中修改，而在另一個定義域中讀取時，在 **\/clr:pure** 之下標示為 `__declspec(process)` 的變數很容易出錯。  
  
 因此，編譯器會在 **\/clr:pure** 之下，強制處理序專屬變數必須為 `const`，讓它們都在所有應用程式定義域中都是唯讀。  
  
 如需詳細資訊，請參閱[處理序](../../cpp/process.md)與[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 下列範例會產生 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```