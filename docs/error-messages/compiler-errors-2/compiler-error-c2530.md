---
title: 編譯器錯誤 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737123"
---
# <a name="compiler-error-c2530"></a>編譯器錯誤 C2530

' identifier '：必須初始化參考

您必須在宣告參考時加以初始化，除非已宣告它：

- 搭配關鍵字[extern](../../cpp/using-extern-to-specify-linkage.md)。

- 做為類別、結構或等位的成員（而且會在此函式中初始化）。

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
