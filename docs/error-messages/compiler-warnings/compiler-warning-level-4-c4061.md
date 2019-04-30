---
title: 編譯器警告 （層級 4） C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401419"
---
# <a name="compiler-warning-level-4-c4061"></a>編譯器警告 （層級 4） C4061

> 列舉值 '*識別碼*'參數中的列舉'*列舉*' case 標籤並未明確處理

指定的列舉值*識別碼*有沒有相關聯的處理常式`switch`具有陳述式`default`案例。 遺失的情況下可能會疏忽，或它可能不是問題。 它可能取決於是否處理列舉程式會由 default case 與否。 未使用的列舉值中的相關警告`switch`沒有任何的陳述式`default`情況下，請參閱[C4062](compiler-warning-level-4-c4062.md)。

此警告預設為關閉。 如需如何啟用預設為關閉的警告的詳細資訊，請參閱[編譯器警告，預設為關閉的](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

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

## <a name="see-also"></a>另請參閱

[編譯器警告 (層級 4) C4062](compiler-warning-level-4-c4062.md)
