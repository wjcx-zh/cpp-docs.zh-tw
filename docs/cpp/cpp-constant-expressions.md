---
title: C + + 常數運算式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35041b3a58f53586702db73d3bc5f6103f4f7cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054359"
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