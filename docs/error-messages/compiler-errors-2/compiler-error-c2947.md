---
title: 編譯器錯誤 C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 3738c257192134eedb8554b0d875023862441416
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566750"
---
# <a name="compiler-error-c2947"></a>編譯器錯誤 C2947

必須以 '>' 結束 construct，但卻找到 'syntax'

使用泛型或樣板引數清單可能不正確地終止。

C2947 也可能會產生語法錯誤。

下列範例會產生 C2947:

```
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```