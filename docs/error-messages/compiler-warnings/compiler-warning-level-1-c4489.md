---
title: 編譯器警告 (層級 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: e9811e9f9c17463fdcd550ffd82af4f81a40bb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186604"
---
# <a name="compiler-warning-level-1-c4489"></a>編譯器警告 (層級 1) C4489

' 規範 '：不允許用在介面方法 ' method ';覆寫規範只允許用於 ref 類別和實值類別方法

在介面方法上不正確地使用了規範關鍵字。

如需詳細資訊，請參閱覆[寫](../../extensions/override-specifiers-cpp-component-extensions.md)規範。

## <a name="example"></a>範例

下列範例會產生 C4489。

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```
