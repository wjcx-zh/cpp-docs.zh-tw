---
title: __unaligned |Microsoft Docs
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
ms.openlocfilehash: 2a7a9de35e225dabadbf9f4a3731f6d57fd9e99a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940409"
---
# <a name="unaligned"></a>__unaligned

**Microsoft 專有**。 當您宣告的指標 **__unaligned**修飾詞，編譯器會假設指標位址未對齊的資料。 因此，適當的平台程式碼會產生以處理未對齊的讀取和寫入透過指標。

## <a name="remarks"></a>備註

此修飾詞描述指標所定址的資料的對齊方式指標本身會假設為對齊。

省略 **__unaligned**關鍵字會因平台和環境而異。 無法適當地標記資料可能會導致問題的硬體故障，舉凡效能的負面影響。 **__Unaligned**修飾詞不是適用於 x86 平台。

如需對齊的詳細資訊，請參閱：

- [align](../cpp/align-cpp.md)

- [__alignof 運算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (結構成員對齊)](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
