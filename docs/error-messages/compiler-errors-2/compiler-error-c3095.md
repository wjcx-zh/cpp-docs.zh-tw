---
title: "編譯器錯誤 C3095 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3095
dev_langs:
- C++
helpviewer_keywords:
- C3095
ms.assetid: cde725be-0936-40f6-9e57-e1d7d0710f83
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a47e7b6ee006bc7a490a01a825a29a265586b0aa
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3095"></a>編譯器錯誤 C3095
'attribute': 屬性不可以重複  
  
 宣告部分屬性，讓屬性的多個項目不能套用至目標。  
  
 如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3095。  
  
```  
// C3095.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All, AllowMultiple=false)]  
public ref class Attr : public Attribute {  
public:  
   Attr(int t) : m_t(t) {}  
   const int m_t;  
};  
  
[AttributeUsage(AttributeTargets::All, AllowMultiple=true)]  
public ref class Attr2 : public Attribute {  
public:  
   Attr2(int t) : m_t(t) {}  
   const int m_t;  
};  
  
[Attr(10)]   // C3095  
[Attr(11)]  
ref class A {};  
  
[Attr2(10)]   // OK  
[Attr2(11)]  
ref class B {};  
```
