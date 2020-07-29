---
title: 在 __asm 區塊中使用 C 或 C++ 符號
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: ecdd3b6b6916a5c9585678838d8e494a58e0508c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191192"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>在 __asm 區塊中使用 C 或 C++ 符號

**Microsoft 特定的**

**`__asm`** 區塊可以在出現區塊的範圍中參考任何 C 或 c + + 符號。 （C 和 c + + 符號是變數名稱、函數名稱和標籤，也就是不是符號常數或成員的名稱 **`enum`** 。 您不能呼叫 C++ 成員函式)。

使用 C 和 C++ 符號時有一些限制：

- 每個組合語言陳述式只能包含一個 C 或 C++ 符號。 多個符號只能出現在具有**LENGTH**、 **TYPE**和**SIZE**運算式的相同元件指令中。

- 區塊中參考的函式 **`__asm`** 必須在程式中稍早宣告為（原型）。 否則，編譯器無法區別區塊中的函式名稱和標籤 **`__asm`** 。

- **`__asm`** 區塊不能將任何 c 或 c + + 符號與 MASM 保留字（不論大小寫為何）使用相同的拼寫。 MASM 保留字包含指令名稱，例如**PUSH**和 register 名稱（例如 SI）。

- 區塊中無法辨識結構和等位標記 **`__asm`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
