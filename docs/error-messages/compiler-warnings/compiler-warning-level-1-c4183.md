---
title: 編譯器警告（層級1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: be79c664f09f80d8f0c8779babf236dccac90ea8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626223"
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