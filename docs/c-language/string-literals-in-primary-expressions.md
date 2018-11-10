---
title: 主要運算式中的字串常值
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
ms.openlocfilehash: 7d228f5ef4209ad47101240cb24429d6d502e9ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521316"
---
# <a name="string-literals-in-primary-expressions"></a>主要運算式中的字串常值

「字串常值」是以雙引號括住的字元、寬字元或一連串相鄰的字元。 由於字串常值不是變數，因此它們本身及擁有的任何項目都不可以是指派運算式的左運算元。 字串常值的類型為 `char` 陣列 (若為寬字串常值則為 `wchar_t` 陣列)。 運算式中的陣列會轉換成指標。 如需字串的詳細資訊，請參閱[字串常值](../c-language/c-string-literals.md)。

## <a name="see-also"></a>請參閱

[C 主要運算式](../c-language/c-primary-expressions.md)