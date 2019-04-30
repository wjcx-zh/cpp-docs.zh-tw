---
title: 編譯器錯誤 C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388853"
---
# <a name="compiler-error-c2279"></a>編譯器錯誤 C2279

例外狀況規格不能出現在 typedef 宣告

底下 **/Za**，[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)typedef 宣告中不允許。

下列範例會產生 C2279:

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```