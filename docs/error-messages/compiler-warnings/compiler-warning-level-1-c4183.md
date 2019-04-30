---
title: 編譯器警告 （層級 1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 0d947a0f6d777a5ed3191d6d232a604028be2003
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391617"
---
# <a name="compiler-warning-level-1-c4183"></a>編譯器警告 （層級 1） C4183

'identifier': 遺漏傳回類型;假設為傳回 'int' 的成員函式

在類別或結構的成員函式的內嵌定義沒有傳回型別。 此成員函式會假設有一個預設的傳回型別`int`。

下列範例會產生 C4183:

```
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```