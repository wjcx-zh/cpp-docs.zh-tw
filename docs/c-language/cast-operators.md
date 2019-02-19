---
title: 轉型運算子
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: e3d892a5aede4cd2d6a980b440875f0ac9837120
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147941"
---
# <a name="cast-operators"></a>轉型運算子

類型轉換提供了一個明確的轉換方法，可在特定情況下轉換物件的類型。

## <a name="syntax"></a>語法

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

在類型轉換完成後，編譯器會將 *cast-expression* 視為 *type-name* 類型。 轉型可用來將任何純量類型的物件與任何其他純量類型的物件來回轉換。 明確類型轉換受限於與判斷隱含轉換效果相同的規則，如[指派轉換](../c-language/assignment-conversions.md)中所討論。 對轉型的其他限制可能來自特定類型的實際大小或表示。 如需整數類型實際大小的詳細資訊，請參閱[基本類型的儲存空間](../c-language/storage-of-basic-types.md)。 如需類型轉型的詳細資訊，請參閱[類型轉換](../c-language/type-cast-conversions.md)。

## <a name="see-also"></a>另請參閱

[轉型運算子：()](../cpp/cast-operator-parens.md)
