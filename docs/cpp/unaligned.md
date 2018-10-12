---
title: __unaligned |Microsoft Docs
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444bc3372b22676cacb3ee89b9c0ad92000cedcc
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161212"
---
# <a name="unaligned"></a>__unaligned

**Microsoft 專有**。 當您宣告的指標 **__unaligned**修飾詞，編譯器會假設指標位址未對齊的資料。 因此，適當的平台程式碼會產生以處理未對齊的讀取和寫入透過指標。

## <a name="remarks"></a>備註

此修飾詞描述指標所定址的資料的對齊方式指標本身會假設為對齊。

省略 **__unaligned**關鍵字會因平台和環境而異。 無法適當地標記資料可能會導致問題的硬體故障，舉凡效能的負面影響。 **__Unaligned**修飾詞不是適用於 x86 平台。

為了與舊版中，相容性 **_unaligned**同義 **__unaligned**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)指定。

如需對齊的詳細資訊，請參閱：

- [align](../cpp/align-cpp.md)

- [__alignof 運算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (結構成員對齊)](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)