---
title: 編譯器警告（層級1） C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051562"
---
# <a name="compiler-warning-level-1-c4804"></a>編譯器警告（層級1） C4804

' operation '：作業中不安全使用類型 ' bool '

當您以非預期的方式使用 `bool` 變數或值時，就會出現這個警告。 例如，如果您使用負一元運算子（ **-** ）或補數運算子（`~`）之類的運算子，則會產生 C4804。 編譯器會評估運算式。

## <a name="example"></a>範例

下列範例會產生 C4804：

```cpp
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