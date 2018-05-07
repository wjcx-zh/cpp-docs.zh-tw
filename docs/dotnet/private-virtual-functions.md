---
title: 私用虛擬函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 97b4d7d9f47901fa69aa50bfc6f405355cf378b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="private-virtual-functions"></a>私用虛擬函式
在衍生類別中處理私用虛擬函式的方式已從 Managed Extensions for c + + Visual c + +。  
  
 在 Managed Extensions，虛擬函式的存取層級不會限制其衍生類別中覆寫的能力。 在新語法中，虛擬函式無法覆寫基底類別虛擬函式，它無法存取。 例如:   
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible  
   void g();  
};  
```  
  
 這種設計新語法中沒有實際的對應。 其中一個只要有將基底類別成員存取-亦即，非私用。 繼承的方法沒有用戶須自行相同的存取權。 在此範例中，至少侵入性功能的變更是對 MyBaseClass 成員`protected`。 如此一來仍然禁止透過 MyBaseClass 方法的一般程式的存取。  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 請注意，如果沒有明確的`virtual`關鍵字在基底類別中，在新語法中，會產生一則警告訊息。  
  
## <a name="see-also"></a>另請參閱  
 [在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 