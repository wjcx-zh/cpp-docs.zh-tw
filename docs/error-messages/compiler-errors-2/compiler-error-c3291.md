---
title: 編譯器錯誤 C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: e3f20d7d7e63079ed9c7a078e9fc9eac06d32677
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781610"
---
# <a name="compiler-error-c3291"></a>編譯器錯誤 C3291

'default' : trivial 屬性不能使用這個名稱

trivial 屬性不可命名為 `default`。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>範例

下列範例會產生 C3291：

```
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```