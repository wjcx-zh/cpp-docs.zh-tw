---
title: 編譯器錯誤 C3252 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70a38090bcbe1a984e643d6d995abe2c79339163
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080619"
---
# <a name="compiler-error-c3252"></a>編譯器錯誤 C3252

'method': 無法縮小 Managed 或 WinRT 類型中虛擬方法的存取範圍

實作基底類別中的虛擬方法或介面中的任何方法的類別，無法縮小該方法的存取範圍。

請注意，介面中的所有方法都是公用。

下列範例會產生 C3252，並示範如何修正此問題：

```
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```