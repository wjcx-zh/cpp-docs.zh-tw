---
title: 在 __asm 區塊中使用 C 或 C++
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 05e63d666f3fc39126d6f48e8fc523c4a02e76df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191413"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>在 __asm 區塊中使用 C 或 C++

**Microsoft 特定的**

由於內嵌組譯碼指令可以與 C 或 C++ 陳述式混用，因此它們可以依名稱參考 C 或 C++ 變數，以及使用這些語言的許多其他項目。

**`__asm`** 區塊可以使用下列語言元素：

- 符號，包括標籤及變數和函式名稱

- 常數，包括符號常數和 **`enum`** 成員

- 巨集和前置處理器指示詞

- __ / \* 批註 \* （ / __和 __//__ ）

- 類型名稱 (MASM 類型為合法的任何位置)

- **`typedef`** 名稱，通常與**PTR**和**類型**之類的運算子搭配使用，或用來指定結構或等位成員

在 **`__asm`** 區塊中，您可以使用 C 標記法或組合器基數標記法來指定整數常數（例如，0x100 和100h 是相等的）。 這樣您就可以在 C 中定義常數 (使用 `#define`)，然後在 C 或 C++ 中與程式的組合語言部分使用該常數。 您也可以在常數前面加上 0，指定八進位的常數。 例如，0777 會指定八進位常數。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [在 __asm 區塊中使用運算子](../../assembler/inline/using-operators-in-asm-blocks.md)

- [在 __asm 區塊中使用 C 或 C++ 符號](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [存取 __asm 區塊中的 C 或 c + + 資料](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [使用內嵌組解碼撰寫函式](../../assembler/inline/writing-functions-with-inline-assembly.md)

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
