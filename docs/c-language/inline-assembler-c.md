---
title: 內嵌組譯工具 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: f6bff3bfef64b45c8a02bb9ad69d2731ba778525
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229606"
---
# <a name="inline-assembler-c"></a>內嵌組譯工具 (C)

**Microsoft 特定的**

內嵌組合語言可讓您直接在 C 原始程式中內嵌組合語言指令，而不需要額外的組合和連結步驟。 內嵌組合語言已內建於編譯器 — 您不需要個別的組譯工具，例如 Microsoft Macro Assembler (MASM)。

因為內嵌組合不需要個別的組譯及連結步驟，所以比個別進行組譯方便。 內嵌組合語言程式碼可以使用範圍內的任何 C 變數或函式名稱，因此很容易就能與您程式的 C 程式碼整合。 而且，因為組譯程式碼可以與 C 陳述式混用，因此能夠執行單獨在 C 中相當麻煩或無法執行的工作。

關鍵字會叫 **`__asm`** 用內嵌組合語言，而且可以出現在 C 語句合法的任何地方。 它不可以單獨出現。 後面必須接著組譯碼指令、放在大括號中的指令群組，或至少是一對空的大括號。 此處的「區塊」一詞 **`__asm`** 指的是任何指令或指示群組，不論是否以大括弧括住。

以下程式碼是 **`__asm`** 以大括弧括住的簡單區塊。 (程式碼是自訂函式初構序列)。

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

或者，您可以 **`__asm`** 在每個元件指令前面放入：

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

由於 **`__asm`** 關鍵字是語句分隔符號，因此您也可以將元件指令放在同一行：

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[函數屬性](../c-language/function-attributes.md)
