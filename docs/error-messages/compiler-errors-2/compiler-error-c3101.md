---
title: 編譯器錯誤 C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: d39afc548010df95bdf31b2c7708bc4fa0310bcd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404191"
---
# <a name="compiler-error-c3101"></a>編譯器錯誤 C3101

具名的屬性引數 'field' 不合法的運算式

當初始化具名的屬性引數，則值必須是編譯時間常數。

如需有關屬性的詳細資訊，請參閱 < [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

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