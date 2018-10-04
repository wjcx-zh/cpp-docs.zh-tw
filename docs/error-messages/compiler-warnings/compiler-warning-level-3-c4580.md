---
title: 編譯器警告 （層級 3） C4580 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cd0b401624ea6815b31b55a7da9c8796746ce8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789198"
---
# <a name="compiler-warning-level-3-c4580"></a>編譯器警告 (層級 3) C4580

[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別

[[屬性](../../windows/attributes/attribute.md)] 已不再建立使用者定義屬性的慣用語的法。 如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。 針對 CLR 程式碼，請從 `System::Attribute` 衍生屬性。 針對 Windows 執行階段程式碼，請從 `Platform::Metadata` 衍生屬性。

## <a name="example"></a>範例

下列範例會產生 C3454，並說明如何加以修正。

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```