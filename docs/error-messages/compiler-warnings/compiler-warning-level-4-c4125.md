---
title: 編譯器警告 (層級 4) C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: f194f0efc8012bf027e4785c2f398a0a7027b368
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991576"
---
# <a name="compiler-warning-level-4-c4125"></a>編譯器警告 (層級 4) C4125

八進位逸出序列結尾有十進位數字

編譯器會評估沒有十進位數字的八進位數字，並假設十進位數字是一個字元。

## <a name="example"></a>範例

```cpp
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

如果數字 9 是要作為字元，請如下更正範例：

```cpp
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```
