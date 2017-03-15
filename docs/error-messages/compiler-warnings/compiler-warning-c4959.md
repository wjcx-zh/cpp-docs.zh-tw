---
title: "編譯器警告 C4959 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4959"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4959"
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4959
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在 \/clr:safe 中定義 Unmanaged 結構 'type'，因為存取它的成員會產生無法驗證的程式碼  
  
 存取 Unmanaged 類型的成員將會產生無法驗證的 \(peverify.exe\) 映像。  
  
 如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [\/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。  
  
 下列範例會產生 C4959：  
  
```  
// C4959.cpp // compile with: /clr:safe // Uncomment the following line to resolve. // #pragma warning( disable : 4959 ) struct X { int data; }; int main() { X x; x.data = 10;   // C4959 }  
```