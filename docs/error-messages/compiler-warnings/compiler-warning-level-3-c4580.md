---
title: "編譯器警告 （層級 3） C4580 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: c8cebbda1d3472a2efda43f816e7a13f2f460408
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4580"></a>編譯器警告 (層級 3) C4580
[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別  
  
[[屬性](../../windows/attribute.md)] 不再是慣用的語法建立使用者定義的屬性。 如需詳細資訊，請參閱[使用者定義屬性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 針對 CLR 程式碼，請從 `System::Attribute` 衍生屬性。 針對 Windows 執行階段程式碼，請從 `Platform::Metadata` 衍生屬性。  
  
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
