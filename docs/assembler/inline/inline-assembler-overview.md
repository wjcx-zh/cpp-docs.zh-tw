---
title: "內嵌組譯工具概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 叫用內嵌組譯工具"
  - "內嵌組譯工具"
  - "內嵌組譯碼, 內嵌組譯工具"
  - "叫用內嵌組譯工具"
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 內嵌組譯工具概觀
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 內嵌組譯工具可讓您在沒有額外的組件和連結步驟 C 和 c \+ \+ 原始檔程式中內嵌組合語言指令。  編譯器內建內嵌組譯工具 — 您不需要個別的組譯工具如 Microsoft 巨集組合語言 \(MASM\)。  
  
 內嵌組譯工具不需要單獨的組件和連結步驟，因為它是比個別的組譯工具更方便。  內嵌組譯程式碼可以使用任何 C 或 c \+ \+ 變數或函式的名稱是在範圍內，因此很容易整合您的程式 C 和 c \+ \+ 程式碼。  與組件程式碼可以混合使用 C 和 c \+ \+ 的陳述式，因為它可以做很麻煩，甚或 C 或 c \+ \+ 單獨的工作。  
  
 [\_\_Asm](../../assembler/inline/asm.md) 關鍵字叫用內嵌組譯工具，而且可以出現 C 或 c \+ \+ 的陳述式是合法的任何地方。  它不可單獨出現。  接下來還必須是組件指示，指示括在大括號，或至少，在一群空組大括號。  詞彙" `__asm`區塊 」 這裡是指任何指令或一群在大括號中的指示。  
  
 下列程式碼是簡單的`__asm`的大括號括住的區塊。  \(程式碼是自訂函式初構序列\)。  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
}  
```  
  
 或者，您可以將`__asm`在每個組件指示：  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 因為`__asm`關鍵字是陳述式分隔符號，您也可以將組譯碼指令放在同一行：  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE  
```  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)