---
title: 編譯器警告 （層級 4） C4232 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 450c764cfc130acf28e3edfb40fcd17c8ac3b664
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118280"
---
# <a name="compiler-warning-level-4-c4232"></a>編譯器警告 (層級 4) C4232

使用非標準擴充: 'identifier': dllimport 'dllimport' 的位址並非靜態，不保證身分識別

Microsoft 擴充功能 (/Ze) 下您可以提供給非靜態值，以宣告的函式的位址**dllimport**修飾詞。 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，這會導致錯誤。

下列範例會產生 C4232:

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```