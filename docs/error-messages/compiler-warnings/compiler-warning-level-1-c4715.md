---
title: 編譯器警告 （層級 1） C4715 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3de829992bfa650280768a2fcd761feaeaece0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061366"
---
# <a name="compiler-warning-level-1-c4715"></a>編譯器警告 (層級 1) C4715

'function': 不是所有控制路徑都傳回值

指定的函式可能不可以傳回值。

## <a name="example"></a>範例

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

若要避免這個警告，請修改程式碼，使所有路徑都指派給函式的傳回值：

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

它是您的程式碼，可能包含呼叫的函式從未返回，如下列範例所示：

```
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

此程式碼也會產生警告，因為編譯器不知道，`fatal`永遠不會傳回。 若要避免這段程式碼產生錯誤訊息，宣告`fatal`使用[__declspec （noreturn)](../../cpp/noreturn.md)。