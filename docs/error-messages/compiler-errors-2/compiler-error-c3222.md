---
title: 編譯器錯誤 C3222 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30231f74b379cd9d69806fbd4b49ba0cb55ad871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048314"
---
# <a name="compiler-error-c3222"></a>編譯器錯誤 C3222

'parameter'：無法對 Managed 或 WinRT 類型或泛型函式的成員函式宣告預設引數

不允許宣告具有預設引數的方法參數。 方法的多載形式是解決這個問題的一種方法。 也就是說，定義不含參數的同名方法，然後在方法主體中初始化變數。

下列範例會產生 C3222：

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
