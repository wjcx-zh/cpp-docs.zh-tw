---
title: 編譯器錯誤 C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 1344bd8bde532d2e813ca03e173b995e935c76b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661314"
---
# <a name="compiler-error-c2569"></a>編譯器錯誤 C2569

'EnumOrUnion': 列舉/等位不能當做基底類別

如果您必須從指定的等位或列舉型別衍生型別，請變更類別或結構的等位或列舉型別。

下列範例會產生 C2569:

```
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```