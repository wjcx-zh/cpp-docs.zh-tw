---
title: 編譯器錯誤 C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: 66b7d70b9010855ada7b9d24fba80915450a685b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301869"
---
# <a name="compiler-error-c2191"></a>編譯器錯誤 C2191

第二個參數清單比第一個更長

第二次使用較長的參數清單宣告了 C 函式。 C 不支援多載函式。

## <a name="example"></a>範例

下列範例會產生 C2191：

```c
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```
