---
title: 編譯器錯誤 C3874
ms.date: 11/04/2016
f1_keywords:
- C3874
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
ms.openlocfilehash: 73476d50b6cfe098ee9d8084837c2090e198a6cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445041"
---
# <a name="compiler-error-c3874"></a>編譯器錯誤 C3874

'function' 傳回型別應該是 'int'，而不是 'type'

函式沒有編譯器所預期的傳回型別。

下列範例會產生 C3874:

```
// C3874b.cpp
double main()
{   // C3874
}
```