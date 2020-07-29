---
title: 具有一元運算子的運算式
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 032ebd99041de9308d16710b2a27e0db3cddd4df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233752"
---
# <a name="expressions-with-unary-operators"></a>具有一元運算子的運算式

一元運算子只會在運算式中的一個運算元上作用。 一元運算子如下：

- [間接取值運算子（*）](../cpp/indirection-operator-star.md)

- [Address 運算子（&）](../cpp/address-of-operator-amp.md)

- [一元加號運算子 (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [一元負運算子（-）](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [邏輯負運算子（！）](../cpp/logical-negation-operator-exclpt.md)

- [一補數運算子（~）](../cpp/one-s-complement-operator-tilde.md)

- [前置遞增運算子 (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [前置遞減運算子（--）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Cast 運算子（）](../cpp/cast-operator-parens.md)

- [`sizeof`操作](../cpp/sizeof-operator.md)

- [`__uuidof`操作](../cpp/uuidof-operator.md)

- [`alignof`操作](../cpp/alignof-operator.md)

- [`new`操作](../cpp/new-operator-cpp.md)

- [`delete`操作](../cpp/delete-operator-cpp.md)

這些運算子具有由右到左的順序關聯性。 一元運算式的語法通常會置於後置或主要運算式的前方。

以下是一元運算式的可能形式。

- *postfix-expression*

- `++` *unary-expression*

- `--` *unary-expression*

- *一元運算子* *cast 運算式*

- **`sizeof`***一元運算式*

- `sizeof(`*類型-名稱*`)`

- `decltype(` *expression* `)`

- *配置運算式*

- *解除配置-運算式*

任何後置*運算式*都會被視為*一元運算式*，而且因為任何主要運算式都會被視為後置*運算式*，所以任何主要運算式也會視為*一元運算式*。 如需詳細資訊，請參閱後置[運算式](../cpp/postfix-expressions.md)和[主要運算式](../cpp/primary-expressions.md)。

*一元運算子*包含下列一個或多個符號：`* & + - ! ~`

*Cast 運算式*是具有選擇性轉換的一元運算式，可變更型別。 如需詳細資訊，請參閱[轉換運算子：（）](../cpp/cast-operator-parens.md)。

*運算式*可以是任何運算式。 如需詳細資訊，請參閱[運算式](../cpp/expressions-cpp.md)。

*配置運算式*會參考 **`new`** 運算子。 *解除配置運算式*會參考 **`delete`** 運算子。 如需詳細資訊，請參閱本主題稍早的連結。

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)
