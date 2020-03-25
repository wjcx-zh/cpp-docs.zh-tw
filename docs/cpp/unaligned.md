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
ms.openlocfilehash: 5f93aaa79fd7c3664ecf80d5007d5954002bce4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160641"
---
# <a name="__unaligned"></a>__unaligned

**Microsoft 特有**。 當您使用 **__unaligned**修飾詞宣告指標時，編譯器會假設指標會定址未對齊的資料。 因此，會產生平臺適當的程式碼，以透過指標來處理未對齊的讀取和寫入。

## <a name="remarks"></a>備註

這個修飾詞會描述指標所定址之資料的對齊方式。指標本身會假設為對齊。

**__Unaligned**關鍵字的必要條件會因平臺和環境而異。 若未適當地標記資料，可能會導致問題，範圍從效能損失到硬體錯誤。 **__Unaligned**修飾詞對 x86 平臺無效。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_unaligned**是 **__unaligned**的同義字。

如需對齊的詳細資訊，請參閱：

- [align](../cpp/align-cpp.md)

- [__alignof 運算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (結構成員對齊)](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
