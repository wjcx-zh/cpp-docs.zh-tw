---
title: "繼承 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50b6b180a6def741daa47a5054f1c61d3265ebd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inheritance--c"></a>繼承 (C++)
本節將說明如何使用衍生類別產生可擴充程式。  
  
## <a name="overview"></a>總覽  
 可以從現有的類別使用稱為 「 繼承 」 的機制衍生新類別 (請參閱資訊一開始[單一繼承](../cpp/single-inheritance.md))。 供衍生使用的類別稱為特定衍生類別的「基底類別」。 衍生類別會使用下列語法宣告：  
  
```  
 class Derived : [virtual] [access-specifier] Base  
{  
   // member list  
};  
 class Derived : [virtual] [access-specifier] Base1,  
 [virtual] [access-specifier] Base2, . . .  
{  
   // member list  
};  
```  
  
 在類別的標記 (名稱) 後方會有一個冒號後面接著基底規格的清單。  基底類別必須先宣告，因此如此命名。  基底規格可能包含存取規範，這是其中一個關鍵字**公用**，`protected`或`private`。  這些存取指定名稱會出現在基底類別名稱的前方，並且只會套用至該基底類別。  這些指定名稱可控制衍生類別使用基底類別成員的權限。  請參閱[成員存取控制](../cpp/member-access-control-cpp.md)如需存取基底類別成員的資訊。  如果省略存取指定名稱，則對該基底的存取會視為是 `private`。  基底規格可能包含關鍵字**虛擬**用於表示虛擬繼承。  這個關鍵字會顯示在存取指定名稱的前方或後方 (如果有的話)。  如果使用虛擬繼承，則會將基底類別稱為是虛擬基底類別。  
  
 您可以指定多個基底類別 (以逗號分隔)。  如果指定單一基底類別，則繼承模型是[單一繼承](../cpp/single-inheritance.md)。如果指定多個基底類別，則繼承模型稱為[多重繼承](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)，  
  
 其中包含下列主題：  
  
-   [單一繼承](../cpp/single-inheritance.md)  
  
-   [多重繼承](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [多重基底類別](../cpp/multiple-base-classes.md)  
  
-   [虛擬函式](../cpp/virtual-functions.md)  
  
-   [明確覆寫](../cpp/explicit-overrides-cpp.md)  
  
-   [抽象類別](../cpp/abstract-classes-cpp.md)  
  
-   [範圍規則摘要](../cpp/summary-of-scope-rules.md)  
  
 [__Super](../cpp/super.md)和[__interface](../cpp/interface.md)關鍵字記載這一節。  
  
## <a name="see-also"></a>請參閱  
 [C++ 語言參考](../cpp/cpp-language-reference.md)