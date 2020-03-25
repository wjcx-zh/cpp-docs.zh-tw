---
title: 編譯器警告（層級1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 4c2c7ce23cfaea5ebf31e78d84b7ff7fbdbf4c85
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175931"
---
# <a name="compiler-warning-level-1-c4183"></a>編譯器警告（層級1） C4183

' identifier '：遺漏傳回類型;假設為傳回 ' int ' 的成員函式

類別或結構中成員函式的內嵌定義沒有傳回型別。 假設這個成員函式具有 `int`的預設傳回型別。

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
