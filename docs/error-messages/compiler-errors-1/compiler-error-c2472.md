---
title: "編譯器錯誤 C2472 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2472"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2472"
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2472
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 無法在 Managed 程式碼中產生: 'message'，請以 \/clr 編譯以便產生混合影像  
  
 在純粹 Common Language Runtime \(CLR\) 環境內使用 Managed 程式碼不支援的類型時，會發生這個錯誤。 請使用 **\/clr** 進行編譯，來解決這個錯誤。  
  
## 範例  
 下列範例會產生 C2472。  
  
```  
// C2472.cpp // compile with: /clr:pure // C2472 expected #include <cstdlib> int main() { int * __ptr32 p32; int * __ptr64 p64; p32 = (int * __ptr32)malloc(4); p64 = p32; }  
```  
  
## 請參閱  
 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)