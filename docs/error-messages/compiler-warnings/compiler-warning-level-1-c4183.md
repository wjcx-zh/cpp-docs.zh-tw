---
title: 編譯器警告 （層級 1） C4183 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4183
dev_langs:
- C++
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2753b8fc47de3363c38ed6ee4dedeaf8d085c485
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022432"
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