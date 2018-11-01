---
title: 編譯器警告 （層級 4） C4061
ms.date: 11/30/2017
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 8b730d561134b8b7ca4454ee74f99216fbc72cb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453263"
---
# <a name="compiler-warning-level-4-c4061"></a>編譯器警告 （層級 4） C4061

> 列舉值 '*識別碼*'參數中的列舉'*列舉*' case 標籤並未明確處理

列舉值有沒有相關聯的處理常式`switch`陳述式。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列範例會產生 C4061;新增遺漏的列舉值，若要修正案例：

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```