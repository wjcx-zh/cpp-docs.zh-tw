---
title: 編譯器錯誤 C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345642"
---
# <a name="compiler-error-c2379"></a>編譯器錯誤 C2379

型式參數數目有不同的類型，當升級

指定參數的型別不相容，透過預設的升級後，先前的宣告中的類型。 這是 ANSI C 中的錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 擴充功能的警告 (**/Ze**)。

下列範例會產生 C2379:

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```