---
title: 編譯器警告 (層級 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: 8a449ee7650196d34d30df646ebdc333c1333af2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161422"
---
# <a name="compiler-warning-level-4-c4202"></a>編譯器警告 (層級 4) C4202

使用非標準的擴充： ' ... '：名稱清單中的原型參數不合法

舊樣式函式定義包含變數引數。 這些定義會在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下產生錯誤。

## <a name="example"></a>範例

```c
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```
