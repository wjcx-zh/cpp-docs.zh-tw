---
title: 私用虛擬函式 |Microsoft Docs
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
ms.openlocfilehash: 0058d023268fa4d9ca5abe802ff45856e9855dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418069"
---
# <a name="private-virtual-functions"></a>私用虛擬函式

在衍生類別中處理私用虛擬函式的方式已經從 Managed Extensions for c + + Visual c + +。

管理擴充功能中的虛擬函式的存取層級不會限制它能夠在衍生類別中覆寫。 在新語法中，虛擬函式無法覆寫基底類別虛擬函式，所以無法存取。 例如: 

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

沒有任何實際的對應，這種設計到新的語法。 只需要讓基底類別成員存取-亦即，非私用可以了。 繼承的方法就不必採取相同的存取。 在此範例中，最不具侵入性的變更是對 MyBaseClass 成員`protected`。 如此一來仍然禁止透過 MyBaseClass 方法的一般程式的存取。

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

請注意，沒有明確的`virtual`關鍵字在基底類別中，在新語法中，會產生一則警告訊息。

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
