---
title: "__thiscall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__thiscall"
  - "__thiscall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__thiscall 關鍵字 [C++]"
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# __thiscall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 專有的  
 `__thiscall` 呼叫慣例用於成員函數，而且是不用變數引數的 C\+\+ 成員函數預設的呼叫慣例。  在 `__thiscall`下，被呼叫端會清除堆疊，在 `vararg` 函式中是不可能的。  在 x86 架構，引數從右至左推入至堆疊，其中 `this` 指標被暫存器 ECX 傳遞，而不是在堆疊上。  
  
 其中一個使用 `__thiscall` 的理由，是在成員函數預設使用 `__clrcall` 的類別中。  在這種情況下，您可以使用 `__thiscall` 讓個別成員函式可在機器碼被呼叫。  
  
 當加入 [\/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)進行編譯時，所有函式和函式指標是 `__clrcall` ，除非另行指定。  
  
 在 Visual C\+\+ 2005 之前的版本，呼叫慣例 thiscall 在程式中無法明確指定，因為 `thiscall` 不是關鍵字。  
  
 `vararg` 成員函式使用 `__cdecl` 呼叫慣例。  所有函式引數都推進堆疊中，其中 `this` 指標最後推入堆疊  
  
 由於這個呼叫慣例僅適用於 C\+\+，因此沒有 C 名稱修飾配置。  
  
 在 ARM 以及 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 電腦上，編譯器會接受並忽略 `__thiscall` 。  
  
 對於非靜態類別函式，如果函式是以非正規的方式定義的，呼叫慣例修飾詞不需要在這個非正規的定義上指定。  也就是，就類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設的。  
  
## 範例  
  
```  
// thiscall_cc.cpp  
// compile with: /c /clr:oldSyntax  
struct CMyClass {  
   void __thiscall mymethod();  
   void __clrcall mymethod2();  
};  
```  
  
## END Microsoft 專有  
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)