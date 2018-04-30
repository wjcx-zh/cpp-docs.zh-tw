---
title: 將 __asm 區塊定義為 C 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69e1e7f2d4b980045a4e8993e39a69fc353a4f39
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="defining-asm-blocks-as-c-macros"></a>將 __asm 區塊定義為 C 巨集
**Microsoft 特定的**  
  
 C 巨集提供便利的方式，可將組譯程式碼插入原始程式碼中，但是，因為巨集會展開成單一邏輯程式敘述行，所以必須特別小心。 為了使建立的巨集不會發生任何錯誤，請遵循這些規則：  
  
-   使用大括號將 `__asm` 區塊括住。  
  
-   將 `__asm` 關鍵字放在每個組譯碼指令前面。  
  
-   使用舊式的 C 註解 ( `/* comment */`) 而不是組譯碼樣式的註解 (`; comment`) 或單行的 C 註解 (`// comment`)。  
  
 為了說明，下列範例會定義一個簡單的巨集：  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 乍看之下，最後三個 `__asm` 關鍵字看起來似乎是多餘的。 不過，因為巨集會展開成單一行，因此它們仍是必要的：  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 第三和第四個 `__asm` 關鍵字也是必要的，做為陳述式分隔符號。 在 `__asm` 區塊中唯一可辨識的陳述式分隔符號為新行字元與 `__asm` 關鍵字。 由於定義為巨集的區塊即是一個邏輯程式敘述行，您必須分隔 `__asm` 中的每個指令。  
  
 大括號也非常重要。 如果您省略它們，編譯器會因為 C 或 C++ 陳述式位於巨集引動過程右邊的同一行而混淆。 少了右邊的大括號，編譯器無法分辨出組譯程式碼從何處停止，因此，它會將 `__asm` 區塊後的 C 或 C++ 陳述式視為組譯碼指令。  
  
 分號為開頭的組譯碼樣式註解 (**;**) 繼續到一行的結尾。 因為編譯器會忽略註釋後方的所有項目，一直到邏輯程式敘述行的結尾，所以會在巨集中產生問題。 同樣的情形也會出現在單行 C 或 C++ 註解 ( `// comment`)。 若要避免這個錯誤，請在定義為巨集的 `/* comment */` 區塊中使用舊式的 C 註解 (`__asm`)。  
  
 以 C 巨集形式撰寫的 `__asm` 區塊可以接受引數。 不過，和一般的 C 巨集不同的是，`__asm` 巨集無法傳回值。 因此您無法在 C 或 C++ 運算式中使用此類的巨集。  
  
 請務必小心，不要隨意叫用此類巨集。 例如，在使用 `__fastcall` 慣例宣告的函式中叫用組合語言巨集可能會導致未預期的結果。 (請參閱[使用和保留暫存器中內嵌組譯碼](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)。)  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)