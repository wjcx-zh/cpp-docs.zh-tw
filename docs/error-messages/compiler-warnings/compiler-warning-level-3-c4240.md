---
title: 編譯器警告 (層級 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: fe5306cc7909138fea0159553b53c2adc6a46dc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402212"
---
# <a name="compiler-warning-level-3-c4240"></a>編譯器警告 (層級 3) C4240

使用非標準擴充： 存取 'classname' 現在已經定義為 '的存取規範'，之前它定義為 '存取規範'

ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，您無法變更的存取權的巢狀類別。 在預設的 Microsoft 擴充功能 (/Ze) 中，您可以使用這項警告。

## <a name="example"></a>範例

```
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```