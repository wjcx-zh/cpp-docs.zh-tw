---
title: 編譯器錯誤 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 32f39eb1d808ccedd27ae3e4d343b87ddfde1862
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174116"
---
# <a name="compiler-error-c3174"></a>編譯器錯誤 C3174

未指定模組屬性

使用視覺效果的程式C++屬性也不是使用[模組](../../windows/module-cpp.md)屬性，都需要使用屬性的任何程式。

下列範例會產生 C3174:

```
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```