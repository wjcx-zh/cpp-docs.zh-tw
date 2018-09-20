---
title: 介面成員的明確覆寫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409021"
---
# <a name="explicit-override-of-an-interface-member"></a>介面成員的明確覆寫

宣告明確的介面成員的類別中覆寫的語法已從 Managed Extensions for c + + Visual c + +。

您通常想要提供介面成員實作介面-一個透過介面控點，管理類別物件時所使用，透過類別介面使用類別物件時使用的另一個類別內的兩個執行個體。 例如: 

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

Managed Extensions 中我們可以提供明確的介面方法宣告介面的名稱來限定方法的名稱。 特定類別的執行個體是不合格。 這就不需要向下轉型的傳回值`Clone`，在此範例中，透過的執行個體的明確呼叫時`R`。

在新語法中，一般的覆寫機制已引進，它會取代 Managed Extensions 的語法。 我們的範例會寫成如下：

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

此修訂可讓您要求明確覆寫介面成員必須指定類別內的唯一名稱。 在這裡，我提供了很冗長，因此名稱`InterfaceClone`。 行為都是一樣-透過引動過程`ICloneable`介面會叫用已重新命名`InterfaceClone`，而類型的物件透過呼叫`R`叫用第二個`Clone`執行個體。

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)