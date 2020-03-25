---
title: 編譯器警告（層級4） C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 84bfef28de2899a216616a6a5d9fb15422f2afec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185408"
---
# <a name="compiler-warning-level-4-c4032"></a>編譯器警告（層級4） C4032

型式參數 ' number ' 在升級時有不同的類型

參數類型與先前宣告中具有類型的預設升級不相容。

這是 ANSI C （[/za](../../build/reference/za-ze-disable-language-extensions.md)）中的錯誤，以及 Microsoft extensions （/ze）底下的警告。

## <a name="example"></a>範例

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```
