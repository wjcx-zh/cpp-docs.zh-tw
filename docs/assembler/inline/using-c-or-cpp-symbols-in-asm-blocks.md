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
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169106"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>在 __asm 區塊中使用 C 或 C++ 符號

**Microsoft 專屬**

一個 `__asm` 區塊可以在出現區塊的範圍中參考任何 C 或 C++ 符號。 (C 和 C++ 符號為變數名稱、函式名稱和標籤，亦即不是符號常數或 `enum` 成員的名稱。 您不能呼叫 C++ 成員函式)。

使用 C 和 C++ 符號時有一些限制：

- 每個組合語言陳述式只能包含一個 C 或 C++ 符號。 多個符號只能出現在具有**LENGTH**、 **TYPE**和**SIZE**運算式的相同元件指令中。

- 在程式的前方必須宣告 (原型) `__asm` 區塊參考的函式。 否則，編譯器無法區分 `__asm` 區塊中的函式名稱和標籤。

- `__asm` 區塊不能使用任何與 MASM 保留字 (不區分大小寫) 相同拼字的 C 或 C++ 符號。 MASM 保留字包含指令名稱，例如**PUSH**和 register 名稱（例如 SI）。

- 在 `__asm` 區塊中無法辨識結構和等位標記。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
