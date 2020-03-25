---
title: 編譯器警告 (層級 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 7dba86d591f18fd7c9c562078204916000d47384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175320"
---
# <a name="compiler-warning-level-1-c4715"></a>編譯器警告 (層級 1) C4715

' function '：並非所有的控制路徑都會傳回值

指定的函式可能不會傳回值。

## <a name="example"></a>範例

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

若要避免這個警告，請修改程式碼，讓所有路徑指派一個傳回值給函數：

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

您的程式碼可能會包含永遠不會傳回之函式的呼叫，如下列範例所示：

```cpp
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

這段程式碼也會產生警告，因為編譯器不知道 `fatal` 絕對不會傳回。 若要避免此程式碼產生錯誤訊息，請使用[__declspec （noreturn）](../../cpp/noreturn.md)宣告 `fatal`。
