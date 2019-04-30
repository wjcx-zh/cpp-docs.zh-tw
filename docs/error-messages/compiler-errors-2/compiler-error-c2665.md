---
title: 編譯器錯誤 C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 63817c4181edb942f43f41c24fb10278d14f397e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386885"
---
# <a name="compiler-error-c2665"></a>編譯器錯誤 C2665

'function': 沒有任何數字 1 多載可以轉換參數數字 2，從類型 'type'

多載函式的參數無法轉換為要求的類型。  可能的解決方式：

- 提供轉換運算子。

- 使用明確轉換。

## <a name="example"></a>範例

下列範例會產生 C2665。

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```