---
title: 具有一元運算子的運算式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 718b27d14414480a3515a212bc0b272e8cfbb7c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017868"
---
# <a name="expressions-with-unary-operators"></a>具有一元運算子的運算式

一元運算子只會在運算式中的一個運算元上作用。 一元運算子如下：

- [間接取值運算子 （*）](../cpp/indirection-operator-star.md)

- [傳址運算子 (&)](../cpp/address-of-operator-amp.md)

- [一元加號運算子 （+）](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [一元負運算子 （-）](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [邏輯負運算子 （！）](../cpp/logical-negation-operator-exclpt.md)

- [一補數運算子 （~）](../cpp/one-s-complement-operator-tilde.md)

- [前置遞增運算子 （+ +）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [前置遞減運算子 （-）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [轉換運算子 （）](../cpp/cast-operator-parens.md)

- [sizeof 運算子](../cpp/sizeof-operator.md)

- [__uuidof 運算子](../cpp/uuidof-operator.md)

- [__alignof 運算子](../cpp/alignof-operator.md)

- [new 運算子](../cpp/new-operator-cpp.md)

- [刪除操作員](../cpp/delete-operator-cpp.md)

這些運算子具有由右到左的順序關聯性。 一元運算式的語法通常會置於後置或主要運算式的前方。

以下是一元運算式的可能形式。

- *postfix-expression*

- `++` *一元運算式*

- `--` *一元運算式*

- *一元運算子* *cast 運算式*

- **sizeof** *一元運算式*

- `sizeof(` *類型名稱* `)`

- `decltype(` *運算式* `)`

- *配置運算式*

- *解除配置運算式*

任何*後置運算式*會被視為*一元運算式*，以及因為任何主要運算式皆視為*後置運算式*，是任何主要運算式被視為*一元運算式*也。 如需詳細資訊，請參閱 <<c0> [ 後置運算式](../cpp/postfix-expressions.md)並[主要運算式](../cpp/primary-expressions.md)。

A*一元運算子*組成一或多個下列符號： `* & + - ! ~`

*轉型運算式*是一元運算式，但若要變更類型的選擇性轉換。 如需詳細資訊，請參閱[轉型運算子: （)](../cpp/cast-operator-parens.md)。

*運算式*可以是任何運算式。 如需詳細資訊，請參閱 <<c0> [ 運算式](../cpp/expressions-cpp.md)。

*配置運算式*是指**新**運算子。 *解除配置運算式*是指**刪除**運算子。 如需詳細資訊，請參閱本主題稍早的連結。

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)