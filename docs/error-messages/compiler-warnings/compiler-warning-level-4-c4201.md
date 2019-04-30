---
title: 編譯器警告 (層級 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: c7c10273e06ec35528dbd9d51c02bb844d275638
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401250"
---
# <a name="compiler-warning-level-4-c4201"></a>編譯器警告 (層級 4) C4201

使用非標準擴充： 沒有名稱的結構/等位

Microsoft 擴充功能 (/Ze) 下您可以指定不含宣告子的結構做為另一個結構或等位的成員。 這些結構產生 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>範例

```
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```