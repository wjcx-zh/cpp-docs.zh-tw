---
title: 編譯器錯誤 C3232
ms.date: 11/04/2016
f1_keywords:
- C3232
helpviewer_keywords:
- C3232
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
ms.openlocfilehash: e0668cb66bf8e9fa6431b6f238167d594cd00416
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750308"
---
# <a name="compiler-error-c3232"></a>編譯器錯誤 C3232

'param': 泛型類型參數不可使用在限定名稱中

泛型類型參數的使用方式錯誤。

下列範例會產生 C3232：

```cpp
// C3232.cpp
// compile with: /clr
generic <class T>
ref class C {
   typename T::TYPE t;   // C3232
};
```
