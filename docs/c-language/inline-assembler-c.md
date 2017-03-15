---
title: "內嵌組譯工具 (C) | Microsoft Docs"
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
  - "__asm 關鍵字 [C]"
  - "內嵌組譯工具 [C]"
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 內嵌組譯工具 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 內嵌組合語言可讓您直接在 C 原始程式中內嵌組合語言指令，而不需要額外的組合和連結步驟。  內嵌組合語言已內建於編譯器 — 您不需要個別的組譯工具，例如 Microsoft Macro Assembler \(MASM\)。  
  
 因為內嵌組合不需要個別的組譯及連結步驟，所以比個別進行組譯方便。  內嵌組合語言程式碼可以使用範圍內的任何 C 變數或函式名稱，因此很容易就能與您程式的 C 程式碼整合。  而且，因為組譯程式碼可以與 C 陳述式混用，因此能夠執行單獨在 C 中相當麻煩或無法執行的工作。  
  
 `__asm` 關鍵字會叫用內嵌組合語言，而且可以出現在 C 陳述式有效的任何地方。  它不可以單獨出現。  後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。  這裡的「`__asm` 區塊」一詞是指任何指令或指令群組，不論是否放在大括號中。  
  
 下列程式碼是放在大括號中的簡單 `__asm` 區塊。\(程式碼是自訂函式初構序列\)。  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
}  
```  
  
 或者，您可以將 `__asm` 放在每個組譯碼指令前面：  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 由於 `__asm` 關鍵字是陳述式分隔符號，您也可以在同一行上放置組譯碼指令：  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE   
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [函式屬性](../c-language/function-attributes.md)