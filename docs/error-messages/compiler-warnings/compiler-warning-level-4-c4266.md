---
title: 編譯器警告 （層級 4） C4266 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4266
dev_langs:
- C++
helpviewer_keywords:
- C4266
ms.assetid: 90ec5f5b-3451-4c16-bb1b-c30a626bdaa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 411654cd70d8dfb241e925112e42bbbcad355597
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023159"
---
# <a name="compiler-warning-level-4-c4266"></a>編譯器警告 (層級 4) C4266

'function': 沒有覆寫的基底 'type'; 虛擬成員函式函式已隱藏

在衍生的類別未覆寫虛擬函式的所有多載。

此警告預設為關閉。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4266:

```
// C4266.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
};   // C4266
```

可能的解決方式：

```
// C4266b.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
   virtual void OnException(int&, int&, int);
};
```