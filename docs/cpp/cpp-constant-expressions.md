---
title: C++ 常數運算式
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576419"
---
# <a name="c-constant-expressions"></a>C++ 常數運算式

A*常數*值是指不會變更。 C++ 提供兩個關鍵字，以讓您表示不要修改物件的意圖，以及施行該意圖。

C++ 需要常數運算式 (也就是評估為常數的運算式) 才能宣告下列各項：

- 陣列界限

- case 陳述式中的選取器

- 位元欄位長度規格

- 列舉初始設定式

常數運算式中合法的運算元包括：

- 常值

- 列舉常數

- 宣告為 const 並使用常數運算式初始化的值

- **sizeof**運算式

非整數常數必須轉換成整數類資料類型 (明確或隱含)，在常數運算式中才會是合法的。 因此，下列程式碼是合法的：

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

明確轉換成整數類資料類型是合法的常數運算式;所有其他類型和衍生型別是除了時做為運算元不合法**sizeof**運算子。

逗號運算子和指派運算子不能在常數運算式中使用。

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)