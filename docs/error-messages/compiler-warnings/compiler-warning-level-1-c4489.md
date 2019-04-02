---
title: 編譯器警告 (層級 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: dd150621ad3474444861982c095ae8a6addb52fa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768233"
---
# <a name="compiler-warning-level-1-c4489"></a>編譯器警告 (層級 1) C4489

'specifier': 不允許在介面方法 'method';覆寫規範只允許在 ref 類別和實值類別方法

介面方法上不正確地使用規範的關鍵字。

如需詳細資訊，請參閱 <<c0> [ 覆寫規範](../../extensions/override-specifiers-cpp-component-extensions.md)。

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