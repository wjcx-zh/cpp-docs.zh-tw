---
title: 編譯器警告 (層級 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: d33e5c60bac657060ffef2a43686a5f737eb11cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161304"
---
# <a name="compiler-warning-level-4-c4212"></a>編譯器警告 (層級 4) C4212

使用非標準的擴充：函式宣告使用了省略號

函式原型有可變數目的引數。 函式定義不是。

下列範例會產生 C4212：

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```
