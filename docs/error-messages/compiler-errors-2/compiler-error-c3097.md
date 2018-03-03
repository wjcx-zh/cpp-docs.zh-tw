---
title: "編譯器錯誤 C3097 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3097
dev_langs:
- C++
helpviewer_keywords:
- C3097
ms.assetid: b24bd8f8-e04f-4fbb-be57-4feb9165572e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98dbe882261040392c9629964b2b1f31cb6b626b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3097"></a>編譯器錯誤 C3097
'attribute': 屬性必須以 'assembly:' 或 'module:' 設定範圍  
  
 不正確地使用了全域屬性。  
  
 如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3097。  
  
```  
// C3097.cpp  
// compile with: /clr /c  
using namespace System;   
  
[AttributeUsage(AttributeTargets::All, AllowMultiple = true)]  
public ref class Attr : public Attribute {  
public:  
   Attr(int t) : m_t(t) {}  
   int m_t;  
};  
  
[Attr(10)];   // C3097  
[assembly:Attr(10)];   // OK  
  
[Attr(10)]   // OK  
public ref class MyClass {};  
```