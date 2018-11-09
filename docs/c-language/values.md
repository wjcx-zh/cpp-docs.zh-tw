---
title: 值
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: e0a200bfea8c0a0a06f064b280dad320da25550c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534052"
---
# <a name="values"></a>值

**ANSI 3.1.2.5**：各種浮點數類型值的表示方式和集合

**float** 類型包含 32 個位元：1 個位元表示正負號、8 個位元表示指數，23 個位元則表示尾數。 其範圍是 +/-3.4E38，且具有至少 7 位數的整數位數。

**double** 類型包含 64 個位元：1 個位元表示正負號、11 個位元表示指數，52 個位元則表示尾數。 其範圍是 +/- 1.7E308，且具有至少 15 位數的整數位數。

**long double** 類型包含 80 個位元：1 個位元表示正負號、15 個位元表示指數，64 個位元則表示尾數。 其範圍是 +/-1.2E4932，且具有至少 19 位數的整數位數。 請注意，在 Microsoft C 編譯器中，**long double** 類型與 **double** 類型的表示方式完全相同。

## <a name="see-also"></a>請參閱

[浮點數學](../c-language/floating-point-math.md)