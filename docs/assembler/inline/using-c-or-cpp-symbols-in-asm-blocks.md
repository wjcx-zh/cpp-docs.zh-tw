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
ms.workload: cplusplus
ms.openlocfilehash: b6a39b747c8c576d148bafff19a664a95fcb43e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>在 __asm 區塊中使用 C 或 C++ 符號
## <a name="microsoft-specific"></a>Microsoft 特定的  
 一個 `__asm` 區塊可以在出現區塊的範圍中參考任何 C 或 C++ 符號。 (C 和 C++ 符號為變數名稱、函式名稱和標籤，亦即不是符號常數或 `enum` 成員的名稱。 您不能呼叫 C++ 成員函式)。  
  
 使用 C 和 C++ 符號時有一些限制：  
  
-   每個組合語言陳述式只能包含一個 C 或 C++ 符號。 多個符號可以出現在相同的組譯碼指令，只能搭配**長度**，**類型**，和**大小**運算式。  
  
-   在程式的前方必須宣告 (原型) `__asm` 區塊參考的函式。 否則，編譯器無法區分 `__asm` 區塊中的函式名稱和標籤。  
  
-   `__asm` 區塊不能使用任何與 MASM 保留字 (不區分大小寫) 相同拼字的 C 或 C++ 符號。 MASM 保留字包括指令名稱，例如**推送**和暫存器名稱 （例如 si）。  
  
-   在 `__asm` 區塊中無法辨識結構和等位標記。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)