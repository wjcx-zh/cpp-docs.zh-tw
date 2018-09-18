---
title: 編譯器警告 （層級 1） C4489 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4489
dev_langs:
- C++
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc019c618a5e4b8a453652573f6f407279792d56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023250"
---
# <a name="compiler-warning-level-1-c4489"></a>編譯器警告 (層級 1) C4489

'specifier': 不允許在介面方法 'method';覆寫規範只允許在 ref 類別和實值類別方法

介面方法上不正確地使用規範的關鍵字。

如需詳細資訊，請參閱 <<c0> [ 覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4489。

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```