---
title: 編譯器錯誤 C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: ee9245fb8eb89b9234e76dc10304b1d05bc1fdcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164835"
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