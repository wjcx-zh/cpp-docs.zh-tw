---
title: 編譯器錯誤 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: da17a3f78c8cab8144cb66b9a672dc59190b50f9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301141"
---
# <a name="compiler-error-c2467"></a>編譯器錯誤 C2467

匿名 ' 使用者定義類型 ' 的宣告不合法

已宣告嵌套的使用者定義型別。 這是在已啟用 ANSI 相容性選項（[/za](../../build/reference/za-ze-disable-language-extensions.md)）的情況下編譯 C 原始程式碼時的錯誤。

下列範例會產生 C2467：

```c
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```
