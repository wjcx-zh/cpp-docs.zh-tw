---
title: 執行階段類型資訊
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: b6d3652539572f094d0e7139e6672402341c956d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232231"
---
# <a name="run-time-type-information"></a>執行階段類型資訊

執行階段類型資訊 (RTTI) 是一項機制，可在程式執行期間判斷物件的類型。 C++ 語言中加入 RTTI 的原因在於，有許多類別庫的廠商本身實作這項功能。 這樣會導致程式庫之間不相容。 因此，在語言層級支援執行階段類型資訊的需求變得很明確。

為避免混淆，這裡討論的 RTTI 幾乎完全限於指標。 不過，所討論的概念也適用於參考。

執行階段類型資訊有三個主要的 C++ 語言項目：

- [Dynamic_cast](../cpp/dynamic-cast-operator.md)運算子。

   用於多型類型的轉換。

- [Typeid](../cpp/typeid-operator.md)運算子。

   用於識別物件的實際類型。

- [Type_info](../cpp/type-info-class.md)類別。

   用來保存由運算子傳回的類型資訊 **`typeid`** 。

## <a name="see-also"></a>另請參閱

[轉型](../cpp/casting.md)
