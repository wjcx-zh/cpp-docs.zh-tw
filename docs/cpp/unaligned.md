---
title: __unaligned |Microsoft 文件
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d73b082b9f41d03eb0b1a8c9fe772351ff4da91f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="unaligned"></a>__unaligned

**Microsoft 特定的**。 當您使用 `__unaligned` 修飾詞宣告指標時，編譯器會假設指標位址資料並未對齊。 因此，適當的平台程式碼會產生以處理未對齊的讀取，並將透過指標。

## <a name="remarks"></a>備註

此修飾詞描述指標; 定址資料的對齊方式指標本身會假設為對齊。

您不再需要的`__unaligned`關鍵字會因平台和環境。 若要適當地標記資料可能導致硬體錯誤到範圍內的效能低落的問題。 `__unaligned`修飾詞不是適用於 x86 平台。

如需對齊的詳細資訊，請參閱：

- [align](../cpp/align-cpp.md)

- [__alignof 運算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (結構成員對齊)](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
