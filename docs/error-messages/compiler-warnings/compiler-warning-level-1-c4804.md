---
title: 編譯器警告 (層級 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406531"
---
# <a name="compiler-warning-level-1-c4804"></a>編譯器警告 (層級 1) C4804

'operation': 不安全的類型 'bool'，在作業中使用

當您使用時，這項警告是針對`bool`變數或值以預期的方式。 如果您使用的運算子，例如負值的一元運算子，例如，產生 C4804 (**-**) 或補充運算子 (`~`)。 編譯器會評估運算式。

## <a name="example"></a>範例

下列範例會產生 C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```