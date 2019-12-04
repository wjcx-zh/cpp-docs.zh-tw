---
title: 編譯器錯誤 C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 7299fe8daa1fa0fc6e1291bf8c683b33235e8bbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755521"
---
# <a name="compiler-error-c2569"></a>編譯器錯誤 C2569

' EnumOrUnion '：列舉/等位不能當做基類使用

如果您必須從指定的聯集或列舉衍生類型，請將聯集或列舉變更為類別或結構。

下列範例會產生 C2569：

```cpp
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```
