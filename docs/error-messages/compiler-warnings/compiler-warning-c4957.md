---
title: "編譯器警告 C4957 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4957"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4957"
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 編譯器警告 C4957
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cast': 無法驗證從 'cast\_from' 明確轉換為 'cast\_to' 的結果  
  
 轉換會產生無法驗證的影像。  
  
 部分轉換是安全的 \(例如，觸發使用者定義轉換的 `static_cast` 以及 `const_cast`\)。[safe\_cast](../../windows/safe-cast-cpp-component-extensions.md) 保證會產生可驗證的程式碼。  
  
 如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [\/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。  
  
 下列範例會產生 C4957：  
  
```  
// C4957.cpp // compile with: /clr:safe // #pragma warning( disable : 4957 ) using namespace System; int main() { Object ^ o = "Hello, World!"; String ^ s = static_cast<String^>(o);   // C4957 String ^ s2 = safe_cast<String^>(o);   // OK }  
```