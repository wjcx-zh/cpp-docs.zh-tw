---
title: 編譯器錯誤 C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 7c1a9e4e099fc33dd585e5cdbffa2bbb8ea36987
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755586"
---
# <a name="compiler-error-c3370"></a>編譯器錯誤 C3370

'idl_module name'：idl_module 尚未定義

您必須先使用 [來指定 DLL 名稱，才能使用](../../windows/idl-module.md) idl_module `idl_module` 指定 DLL 中的進入點。

下列範例會產生 C3370：

```cpp
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```
