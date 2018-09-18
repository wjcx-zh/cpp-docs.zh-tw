---
title: 編譯器警告 （層級 3） C4265 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4265
dev_langs:
- C++
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df54714038ab0fb6020e34aa35d677af5e899b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016126"
---
# <a name="compiler-warning-level-3-c4265"></a>編譯器警告 (層級 3) C4265

'class': 類別有虛擬函式，但不是虛擬解構函式

當類別具有虛擬函式但非虛擬解構函式時，類型的物件可能不會終結正確時終結類別之前透過基底類別指標。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4265:

```
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```