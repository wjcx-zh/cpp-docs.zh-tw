---
title: 編譯器警告 （層級 3） C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402277"
---
# <a name="compiler-warning-level-3-c4159"></a>編譯器警告 （層級 3） C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma(pop,...)： 已經推出之前推入的識別項 '*識別碼*'

## <a name="remarks"></a>備註

您的原始程式碼包含**推播**pragma 的識別項指示後接**pop**沒有識別項的指示。 如此一來，*識別碼*是快顯，及後續使用*識別項*可能會導致非預期的行為。

## <a name="example"></a>範例

若要避免這個警告，請中提供一個識別項**pop**指令。 例如：

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```