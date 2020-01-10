---
title: 編譯器錯誤 C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: f096791a6120023e079b93452a4b35c669db2139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302103"
---
# <a name="compiler-error-c2379"></a>編譯器錯誤 C2379

正式參數編號在升級時有不同的類型

指定參數的類型與先前宣告中類型的預設升級不相容。 這是 ANSI C （[/za](../../build/reference/za-ze-disable-language-extensions.md)）中的錯誤，以及 Microsoft extensions （ **/ze**）的警告。

下列範例會產生 C2379：

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
