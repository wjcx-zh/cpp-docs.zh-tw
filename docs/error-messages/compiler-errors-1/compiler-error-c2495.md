---
title: 編譯器錯誤 C2495
ms.date: 11/04/2016
f1_keywords:
- C2495
helpviewer_keywords:
- C2495
ms.assetid: bb7066fe-3549-4901-97e4-157f3c04dd57
ms.openlocfilehash: 83a0359fce175b12dd18e2500d63d7a86bed9f0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360849"
---
# <a name="compiler-error-c2495"></a>編譯器錯誤 C2495

'identifier': 'nothrow' 只能套用至函式宣告或定義

[Nothrow](../../cpp/nothrow-cpp.md)擴充的屬性可以套用至函式宣告或定義只。

下列範例會產生 C2495:

```
// C2495.cpp
// compile with: /c
__declspec(nothrow) class X {   // C2495
   int m_data;
} x;

__declspec(nothrow) void test();   // OK
```