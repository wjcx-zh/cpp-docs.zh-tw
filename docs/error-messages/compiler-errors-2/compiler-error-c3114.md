---
title: "編譯器錯誤 C3114 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3114
dev_langs:
- C++
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e4ec82d31e26b33364a73384aae08f6adc48da02
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3114"></a>編譯器錯誤 C3114
'argument': 不是有效的具名屬性引數  
  
 為了讓屬性類別資料成員為有效的具名引數，它不能標示`static`， `const`，或`literal`。 如果屬性，屬性不能`static`並且必須有 get 和 set 存取子。  
  
 如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)和[使用者定義的屬性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3114。  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```
