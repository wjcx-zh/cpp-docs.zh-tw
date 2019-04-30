---
title: 編譯器錯誤 C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 0cd27da4b73732513afe0bd33a2d7312e6ddbe97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388721"
---
# <a name="compiler-error-c3369"></a>編譯器錯誤 C3369

'module name': 已定義 idl_module

定義 DLL 的 [idl_module](../../windows/idl-module.md) 用法只能在程式中出現一次。

下列範例會產生 C3369：

```
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```