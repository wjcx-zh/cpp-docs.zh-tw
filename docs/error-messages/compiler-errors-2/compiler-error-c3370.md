---
title: 編譯器錯誤 C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 0dbc95fcb26354b0f963d1844ddd6a43783c532a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466166"
---
# <a name="compiler-error-c3370"></a>編譯器錯誤 C3370

'idl_module name'：idl_module 尚未定義

您必須先使用 [來指定 DLL 名稱，才能使用](../../windows/idl-module.md) idl_module `idl_module` 指定 DLL 中的進入點。

下列範例會產生 C3370：

```
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