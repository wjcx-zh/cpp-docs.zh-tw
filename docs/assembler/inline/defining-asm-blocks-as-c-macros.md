---
title: 將 __asm 區塊定義為 C 巨集
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: 4195624078c53f6c1f20cd2a03ed53dac937d9cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192102"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>將 __asm 區塊定義為 C 巨集

**Microsoft 特定的**

C 巨集提供便利的方式，可將組譯程式碼插入原始程式碼中，但是，因為巨集會展開成單一邏輯程式敘述行，所以必須特別小心。 為了使建立的巨集不會發生任何錯誤，請遵循這些規則：

- **`__asm`** 以大括弧括住區塊。

- 將 **`__asm`** 關鍵字放在每個元件指令前面。

- 使用舊式的 C 註解 ( `/* comment */`) 而不是組譯碼樣式的註解 (`; comment`) 或單行的 C 註解 (`// comment`)。

為了說明，下列範例會定義一個簡單的巨集：

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

乍看之下，最後三個 **`__asm`** 關鍵字看起來是多餘的。 不過，因為巨集會展開成單一行，因此它們仍是必要的：

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

第三個和第四個 **`__asm`** 關鍵字是語句分隔符號所需。 區塊中唯一可識別的語句分隔符號 **`__asm`** 是分行符號和 **`__asm`** 關鍵字。 因為定義為宏的區塊是一個邏輯行，所以您必須使用來分隔每個指令 **`__asm`** 。

大括號也非常重要。 如果您省略它們，編譯器會因為 C 或 C++ 陳述式位於巨集引動過程右邊的同一行而混淆。 如果沒有右大括弧，編譯器就無法分辨元件程式碼的停止位置，而且它會在區塊之後看到 C 或 c + + 語句 **`__asm`** 做為元件指令。

以分號（**;**）開頭的元件樣式批註會繼續到行尾。 因為編譯器會忽略註釋後方的所有項目，一直到邏輯程式敘述行的結尾，所以會在巨集中產生問題。 同樣的情形也會出現在單行 C 或 C++ 註解 ( `// comment`)。 若要避免發生錯誤，請 `/* comment */` 在定義為宏的區塊中使用舊樣式的 C 批註（） **`__asm`** 。

**`__asm`** 以 C 宏撰寫的區塊可以接受引數。 不過，與一般 C 宏不同的是， **`__asm`** 宏無法傳回值。 因此您無法在 C 或 C++ 運算式中使用此類的巨集。

請務必小心，不要隨意叫用此類巨集。 比方說，在使用慣例所宣告的函式中叫用組合語言宏 **`__fastcall`** 可能會導致非預期的結果。 （請參閱[在內嵌元件中使用和保留](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)暫存器）。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
