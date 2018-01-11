---
title: "密封虛擬函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48d52a2697289197555438847ba2fcb86aeb3235
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="sealing-a-virtual-function"></a>密封虛擬函式
密封虛擬函式的語法已從 Managed Extensions for c + + Visual c + +。  
  
 `__sealed`關鍵字用以管理擴充功能中修改任何參考類型，不允許後續從它衍生 (請參閱[的受管理的類別類型宣告](../dotnet/declaration-of-a-managed-class-type.md))，或修改虛擬函式，不允許後續的覆寫衍生類別中的方法。 例如:   
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 在此範例中，`derived::f()`會覆寫`base::f()`根據函式原型完全相符的執行個體。 `__sealed`關鍵字表示後續的類別繼承自衍生類別不能提供的覆寫`derived::f()`。  
  
 在新語法中，`sealed`放之後簽章，而不是可實際函式原型之前，如先前允許任何位置出現。 此外，使用`sealed`需要明確使用`virtual`以及關鍵字。 也就是正確的翻譯`derived`、 以上版本，如下所示：  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 如果沒有`virtual`這個執行個體中的關鍵字會導致錯誤。 在新語法，也就是內容關鍵字`abstract`可用取代`=0`表示純虛擬函式。 這不是支援 Managed Extensions。 例如:   
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 可以重寫為  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>請參閱  
 [在類別或介面中的成員宣告 (C + + /CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)