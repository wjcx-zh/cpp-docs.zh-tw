---
title: 編譯器錯誤 C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: f5799511575617ad1705bbce50a939ee46599628
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755339"
---
# <a name="compiler-error-c3285"></a>編譯器錯誤 C3285

不能在類型 'type' 的變數上使用 for each 陳述式

`for each` 陳述式會為陣列或物件集合中的每個項目，重複一組內嵌陳述式。

如需詳細資訊，請參閱 [for each, in](../../dotnet/for-each-in.md) 。

## <a name="example"></a>範例

下列範例會產生 C3285。

```cpp
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```
