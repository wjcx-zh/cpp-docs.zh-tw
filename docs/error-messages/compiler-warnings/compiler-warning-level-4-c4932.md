---
title: "編譯器警告 (層級 4) C4932 | Microsoft Docs"
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
  - "C4932"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4932"
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4932
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法分辨 \_\_identifier\(identifier\) 和 \_\_identifier\(identifier\)  
  
 編譯器無法區分作為參數傳遞給 [\_\_identifier](../../windows/identifier-cpp-cli.md) 的 **\_finally** 與 `__finally` 或 `__try` 與 **\_try**。 您不應該嘗試同時使用它們作為相同程式中的識別項，因為它會導致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 錯誤。  
  
 下列範例會產生 C4932：  
  
```  
// C4932.cpp // compile with: /clr /W4 /WX int main() { int __identifier(_finally) = 245;   // C4932 int __identifier(__finally) = 25;   // C4932 }  
```