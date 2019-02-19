---
title: 值
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: a745b9cc45ed3e58cab4ec7355707d93a0557c04
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150034"
---
# <a name="values"></a>值

**ANSI 3.1.2.5**：各種浮點數類型值的表示方式和集合

**浮點數**型別包含 32 個位元：1 表示正負號，8 表示指數，23 則表示尾數。 其範圍是 +/-3.4E38，且具有至少 7 位數的整數位數。

**雙精度**型別包含 64 個位元：1 表示正負號，11 表示指數，52 則表示尾數。 其範圍是 +/- 1.7E308，且具有至少 15 位數的整數位數。

**長雙精度**型別包含 80 個位元：1 表示正負號，15 表示指數，64 則表示尾數。 其範圍是 +/-1.2E4932，且具有至少 19 位數的整數位數。 請注意，在 Microsoft C 編譯器中，**long double** 類型與 **double** 類型的表示方式完全相同。

## <a name="see-also"></a>另請參閱

[浮點數學](../c-language/floating-point-math.md)
