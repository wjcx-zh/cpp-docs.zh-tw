---
title: 編譯器錯誤 C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: b1345fbb44558db01b19eec04b64cf7aa036931a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301921"
---
# <a name="compiler-error-c2142"></a>編譯器錯誤 C2142

函式宣告不同，只指定其中一個變數參數

函數的其中一個宣告包含變數參數清單。 另一個宣告則不會。 僅限 ANSI C （[/za](../../build/reference/za-ze-disable-language-extensions.md)）。

下列範例會產生 C2142：

```c
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```
