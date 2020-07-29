---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 2ab94a44d08165ca6e8f394278e24d7c8d201398
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223495"
---
# <a name="__unaligned"></a>__unaligned

**Microsoft 特有**。 當您使用修飾詞宣告指標時 **`__unaligned`** ，編譯器會假設指標會定址未對齊的資料。 因此，會產生平臺適當的程式碼，以透過指標來處理未對齊的讀取和寫入。

## <a name="remarks"></a>備註

這個修飾詞會描述指標所定址之資料的對齊方式。指標本身會假設為對齊。

關鍵字的必要條件會 **`__unaligned`** 因平臺和環境而異。 若未適當地標記資料，可能會導致問題，範圍從效能損失到硬體錯誤。 **`__unaligned`** 修飾詞對 x86 平臺無效。

為了與舊版相容， **`_unaligned`** **`__unaligned`** 除非指定了編譯器選項 [停用[ `/Za` \( 語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能]，否則會是同義字。

如需對齊的詳細資訊，請參閱：

- [`align`](../cpp/align-cpp.md)

- [`alignof`操作](../cpp/alignof-operator.md)

- [`pack`](../preprocessor/pack.md)

- [`/Zp`（結構成員對齊）](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
