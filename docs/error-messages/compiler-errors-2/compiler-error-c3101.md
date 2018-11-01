---
title: 編譯器錯誤 C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: 8db1ba622a0c83a7f2a6421d79ff5853cbc4d9a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555554"
---
# <a name="compiler-error-c3101"></a>編譯器錯誤 C3101

具名的屬性引數 'field' 不合法的運算式

當初始化具名的屬性引數，則值必須是編譯時間常數。

如需有關屬性的詳細資訊，請參閱 < [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3101。

```
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```