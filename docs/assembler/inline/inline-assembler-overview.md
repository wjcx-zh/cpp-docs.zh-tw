---
title: 內嵌組譯工具概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31b0497f2fdc319115018a05618d3a16607dbef1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="inline-assembler-overview"></a>內嵌組譯工具概觀
**Microsoft 特定的**  
  
 內嵌組合語言可讓您在 C 和 C++ 來源程式中內嵌組合語言指令，而不需要額外的組合和連結步驟。 內嵌組合語言已內建於編譯器 — 您不需要個別的組譯工具，例如 Microsoft Macro Assembler (MASM)。  
  
 因為內嵌組合不需要個別的組譯及連結步驟，所以比個別進行組譯方便。 內嵌組譯程式碼可以使用範圍內的任何 C 或 C++ 變數或函式名稱，因此很容易就能與您程式的 C 和 C++ 程式碼整合。 而且，因為組譯程式碼可以與 C 和 C++ 陳述式混用，因此能夠執行單獨在 C 或 C++ 中相當麻煩或無法執行的工作。  
  
 [__Asm](../../assembler/inline/asm.md)關鍵字會叫用內嵌組合語言，而且可以出現在 C 或 c + + 陳述式是合法的任一處。 它不可以單獨出現。 後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。 這裡的「`__asm` 區塊」一詞是指任何指令或指令群組，不論是否放在大括號中。  
  
 下列程式碼是放在大括號中的簡單 `__asm` 區塊。 (程式碼是自訂函式初構序列)。  
  
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)