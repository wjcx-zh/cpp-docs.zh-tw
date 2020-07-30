---
title: 編譯器警告（層級1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: cff62c18442cd6d55a9444bb86944b691145b9fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231919"
---
# <a name="compiler-warning-level-1-c4183"></a>編譯器警告（層級1） C4183

' identifier '：遺漏傳回類型;假設為傳回 ' int ' 的成員函式

類別或結構中成員函式的內嵌定義沒有傳回型別。 假設這個成員函式具有的預設傳回型別 **`int`** 。

下列範例會產生 C4183：

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```
