---
title: "在 __asm 區塊中使用 C 或 c + + 符號 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffa5891cf42b930581fc94c3f39942872f030d0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>在 __asm 區塊中使用 C 或 C++ 符號
## <a name="microsoft-specific"></a>Microsoft 特定的  
 一個 `__asm` 區塊可以在出現區塊的範圍中參考任何 C 或 C++ 符號。 (C 和 C++ 符號為變數名稱、函式名稱和標籤，亦即不是符號常數或 `enum` 成員的名稱。 您不能呼叫 C++ 成員函式)。  
  
 使用 C 和 C++ 符號時有一些限制：  
  
-   每個組合語言陳述式只能包含一個 C 或 C++ 符號。 多個符號可以出現在相同的組譯碼指令，只能搭配**長度**，**類型**，和**大小**運算式。  
  
-   在程式的前方必須宣告 (原型) `__asm` 區塊參考的函式。 否則，編譯器無法區分 `__asm` 區塊中的函式名稱和標籤。  
  
-   `__asm` 區塊不能使用任何與 MASM 保留字 (不區分大小寫) 相同拼字的 C 或 C++ 符號。 MASM 保留字包括指令名稱，例如**推送**和暫存器名稱 （例如 si）。  
  
-   在 `__asm` 區塊中無法辨識結構和等位標記。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)