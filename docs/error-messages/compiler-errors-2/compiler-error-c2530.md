---
title: 編譯器錯誤 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 4eca5579f6bf132452a813d8dd99193df5f76b92
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500544"
---
# <a name="compiler-error-c2530"></a>編譯器錯誤 C2530

' identifier '：必須初始化參考

除非已宣告參考，否則您必須在宣告時初始化參考：

- 使用關鍵字 [extern](../../cpp/extern-cpp.md)。

- 做為類別、結構或等位的成員 (，並在) 的函式中初始化。

- 做為函式宣告或定義中的參數。

- 做為函式的傳回型別。

下列範例會產生 C2530：

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
