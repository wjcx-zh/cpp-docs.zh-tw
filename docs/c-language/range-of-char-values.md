---
title: char 值的範圍
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 085f7a319cb193f9d9d744d6e896062e550404cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227799"
---
# <a name="range-of-char-values"></a>char 值的範圍

**ANSI 3.2.1.1**「純量」是否 **`char`** 有與或相同的值範圍 **`signed char`****`unsigned char`**

從 -128 到 127 的範圍中所有帶正負號的字元值。 從 0 到 255 的範圍中所有不帶正負號的字元值。

編譯器選項會將的 [`/J`](../build/reference/j-default-char-type-is-unsigned.md) 預設類型從變更為 **`char`** **`signed char`** **`unsigned char`** 。

## <a name="see-also"></a>另請參閱

[長度](../c-language/characters.md)
