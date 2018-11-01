---
title: 編譯器錯誤 C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 2c8164cad25d68ee61ff9fed7170482d5dfc9505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474785"
---
# <a name="compiler-error-c2530"></a>編譯器錯誤 C2530

'identifier': 必須初始化參考

您必須初始化參考時宣告它，除非它已經宣告為：

- 以關鍵字[extern](../../cpp/using-extern-to-specify-linkage.md)。

- 類別、 結構或等位的成員身分 （和其建構函式中初始化）。

- 為函式宣告或定義中的參數。

- 函式的傳回型別。

下列範例會產生 C2530:

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```