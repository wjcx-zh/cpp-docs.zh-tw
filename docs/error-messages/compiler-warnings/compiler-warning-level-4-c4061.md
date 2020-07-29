---
title: 編譯器警告（層級4） C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 18c5a51e24af36c5a330e10a66ce3dcc38295fb1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225276"
---
# <a name="compiler-warning-level-4-c4061"></a>編譯器警告（層級4） C4061

> case 標籤未明確處理列舉 '*enumeration*' 的 switch 中的列舉值 '*identifier*'

指定的列舉值*識別碼*在具有案例的語句中沒有相關聯的處理常式 **`switch`** **`default`** 。 遺漏的情況可能是監督，或可能不是問題。 這可能取決於列舉值是否由預設的案例處理。 如需不含任何案例之語句中未使用之列舉值的相關警告 **`switch`** **`default`** ，請參閱[C4062](compiler-warning-level-4-c4062.md)。

此警告預設為關閉。 如需如何啟用預設為關閉之警告的詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>範例

下列範例會產生 C4061;新增遺漏列舉值的案例以修正：

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

## <a name="see-also"></a>另請參閱

[編譯器警告（層級4） C4062](compiler-warning-level-4-c4062.md)
