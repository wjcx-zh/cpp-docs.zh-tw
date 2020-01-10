---
title: 編譯器錯誤 C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: 027c7f49b361ef3aa06a4d74e10f0ff27331b4a9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301882"
---
# <a name="compiler-error-c2190"></a>編譯器錯誤 C2190

第一個參數清單長度超過秒

第二次使用較短的參數清單宣告了 C 函式。 C 不支援多載函式。

下列範例會產生 C2190：

```c
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```
