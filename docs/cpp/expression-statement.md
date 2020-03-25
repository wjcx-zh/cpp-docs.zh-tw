---
title: 運算陳述式
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2f12bbbafd9be50f851e36f472098431f9ac0d5d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188996"
---
# <a name="expression-statement"></a>運算陳述式

運算陳述式會造成對於運算式的評估。 運算陳述式不會發生控制權轉移或反覆項目的情形。

運算陳述式的語法很簡單

## <a name="syntax"></a>語法

```
[expression ] ;
```

## <a name="remarks"></a>備註

在下一個陳述式執行之前，會完成運算陳述式中所有運算式的評估，以及所有副作用。 最常見的運算陳述式是指派和函式呼叫。  因為運算式是選擇性的，所以會將分號單獨視為空的運算式語句，稱為[null](../cpp/null-statement.md)語句。

## <a name="see-also"></a>另請參閱

[C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)
