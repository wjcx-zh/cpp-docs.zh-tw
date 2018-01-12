---
title: "介面成員的明確覆寫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 85681b2e2aeeb6dbeb6ffdf511827fb1fc1cb029
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-override-of-an-interface-member"></a>介面成員的明確覆寫
宣告明確介面成員的類別中覆寫的語法已從 Managed Extensions for c + + Visual c + +。  
  
 您通常想要提供介面成員實作介面的一個透過介面控點，管理類別物件時所使用，透過類別介面使用類別物件時使用的另一個類別內的兩個執行個體。 例如:   
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 在 Managed Extensions 要執行此作業的明確宣告介面方法提供的介面名稱來限定方法的名稱。 類別的特定執行個體是不合格。 這就不需要向下轉型的傳回值`Clone`，在此範例中，透過執行個體的明確呼叫時`R`。  
  
 在新語法中，覆寫一般機制已經導入，以取代 Managed Extensions 語法。 我們的範例會重寫，如下所示：  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 這項修訂要求明確覆寫介面成員必須指定類別內的唯一名稱。 我在這裡，提供了造成不便名稱`InterfaceClone`。 行為方法仍然相同-的引動過程，透過`ICloneable`介面會叫用已重新命名`InterfaceClone`，而透過類型的物件呼叫`R`叫用第二個`Clone`執行個體。  
  
## <a name="see-also"></a>請參閱  
 [在類別或介面中的成員宣告 (C + + /CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)