---
title: 編譯器警告 （層級 3） C4580 |Microsoft 文件
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
ms.openlocfilehash: 89ad08af77b62cd0992e9415e2df8b31233e4e0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290978"
---
# <a name="compiler-warning-level-3-c4580"></a>編譯器警告 (層級 3) C4580
[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別  
  
[[屬性](../../windows/attribute.md)] 不再建立使用者定義屬性的慣用語的法。 如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。 針對 CLR 程式碼，請從 `System::Attribute` 衍生屬性。 針對 Windows 執行階段程式碼，請從 `Platform::Metadata` 衍生屬性。  
  
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