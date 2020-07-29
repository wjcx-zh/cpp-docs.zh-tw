---
title: 類型轉換 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
ms.openlocfilehash: 7d7c55c15a8f3e2a53e350da947cf524ae064a09
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231425"
---
# <a name="type-conversions-c"></a>類型轉換 (C)

類型轉換取決於指定的運算子以及運算元或運算子的類型。 下列情況會執行類型轉換：

- 將某一類型的值指派給另一個類型的變數，或者運算子在執行運算之前轉換其運算元的類型時

- 將某一類型的值明確轉換為不同的類型時

- 將值當作引數傳遞至函式，或者從函式傳回類型時

只要是可以使用整數的運算式，皆可使用字元、短整數或整數位元欄位 (無論是否有帶正負號) 或屬於列舉類型的物件。 如果 **`int`** 可以代表原始類型的所有值，則會將值轉換為， **`int`** 否則會轉換成 **`unsigned int`** 。 這個程序稱為「整數提升」。 整數提升會保留值。 也就是，保證提升後的值會和提升之前一樣。 如需詳細資訊，請參閱[一般算術轉換](../c-language/usual-arithmetic-conversions.md)。

## <a name="see-also"></a>另請參閱

[運算式和指派](../c-language/expressions-and-assignments.md)
