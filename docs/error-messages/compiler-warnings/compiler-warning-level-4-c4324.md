---
title: 編譯器警告 (層級 4) C4324
ms.date: 11/04/2016
f1_keywords:
- C4324
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
ms.openlocfilehash: e4ae270af2a88630f33e677638a5a94b77add601
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991366"
---
# <a name="compiler-warning-level-4-c4324"></a>編譯器警告 (層級 4) C4324

' struct_name '：結構因 __declspec 而填補（align （））

因為您指定了[__declspec （align）](../../cpp/align-cpp.md)值，所以在結構結尾處已加入填補。

例如，下列程式碼會產生 C4324：

```cpp
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```
