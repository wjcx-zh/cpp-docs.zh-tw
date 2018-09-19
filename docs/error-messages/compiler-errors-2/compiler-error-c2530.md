---
title: 編譯器錯誤 C2530 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f41f9ec64e2074ed5e0cd2654f2b6bfec886bc07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103180"
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