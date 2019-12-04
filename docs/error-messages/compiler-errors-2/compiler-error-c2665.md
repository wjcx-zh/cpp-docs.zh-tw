---
title: 編譯器錯誤 C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756015"
---
# <a name="compiler-error-c2665"></a>編譯器錯誤 C2665

' function '：無數位多載可以從類型 ' type ' 轉換參數數位2

多載函式的參數無法轉換成所需的類型。  可能的解決方式：

- 提供轉換運算子。

- 使用明確轉換。

## <a name="example"></a>範例

下列範例會產生 C2665。

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
