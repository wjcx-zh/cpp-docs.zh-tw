---
title: 編譯器錯誤 C3809 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3809
dev_langs:
- C++
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b99cda2ab1790ce63ecbd0f6c5a3dc4d916d34c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104214"
---
# <a name="compiler-error-c3809"></a>編譯器錯誤 C3809

'class'：Managed 或 WinRT 類型不可以有任何的 friend 函式/類別/介面

Managed 類型和 Windows 執行階段類型不允許 friends。 若要修正這個錯誤，請不要在 Managed 或 Windows 執行階段類型中宣告 friends。

下列範例會產生 C3809：

```
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```