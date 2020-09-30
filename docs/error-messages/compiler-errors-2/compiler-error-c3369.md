---
title: 編譯器錯誤 C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 3b2e6f38e93514154b20e674139a2d771dcf586e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503245"
---
# <a name="compiler-error-c3369"></a>編譯器錯誤 C3369

'module name': 已定義 idl_module

定義 DLL 的 [idl_module](../../windows/attributes/idl-module.md) 用法只能在程式中出現一次。

下列範例會產生 C3369：

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
