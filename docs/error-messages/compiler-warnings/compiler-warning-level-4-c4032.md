---
title: 編譯器警告 （層級 4） C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: fa1602d63ed9822725fea8e1b842929f221d3926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401458"
---
# <a name="compiler-warning-level-4-c4032"></a>編譯器警告 （層級 4） C4032

型式參數 'number' 有不同的類型，當升級

參數類型不相容，透過預設的升級後，先前的宣告中的類型。

這是 ANSI C 中的錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和 Microsoft 擴充功能 (/Ze) 下的警告。

## <a name="example"></a>範例

```
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```