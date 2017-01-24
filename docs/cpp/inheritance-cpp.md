---
title: "繼承 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], 衍生"
  - "衍生類別"
  - "衍生類別, 關於衍生類別"
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 繼承 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節將說明如何使用衍生類別產生可擴充程式。  
  
## 概觀  
 新的類別可以使用稱為「繼承」的機制，從現有的類別衍生 \(請參閱[單一繼承](../cpp/single-inheritance.md)中一開始的資訊\)。  供衍生使用的類別稱為特定衍生類別的「基底類別」。  衍生類別會使用下列語法宣告：  
  
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
  
 在類別的標記 \(名稱\) 後方會有一個冒號後面接著基底規格的清單。  基底類別必須先宣告，因此如此命名。  基底規格可能包含存取指定名稱，可能是 **public**、`protected` 或 `private` 其中一個關鍵字。  這些存取指定名稱會出現在基底類別名稱的前方，並且只會套用至該基底類別。  這些指定名稱可控制衍生類別使用基底類別成員的權限。  如需存取基底類別成員的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。  如果省略存取指定名稱，則對該基底的存取會視為是 `private`。  基底規格可能包含關鍵字 **virtual**，用於表示虛擬繼承。  這個關鍵字會顯示在存取指定名稱的前方或後方 \(如果有的話\)。  如果使用虛擬繼承，則會將基底類別稱為是虛擬基底類別。  如需詳細資訊，請參閱[虛擬基底類別](../misc/virtual-base-classes.md)。  
  
 您可以指定多個基底類別 \(以逗號分隔\)。  如果指定了單一基底類別，則繼承模型為[單一繼承](../cpp/single-inheritance.md)。如果指定了一個以上的基底類別，則繼承模型稱為[多重繼承](http://msdn.microsoft.com/zh-tw/3b74185e-2beb-4e29-8684-441e51d2a2ca)、  
  
 其中包含下列主題：  
  
-   [單一繼承](../cpp/single-inheritance.md)  
  
-   [多重繼承](http://msdn.microsoft.com/zh-tw/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [多重基底類別](../cpp/multiple-base-classes.md)  
  
-   [虛擬基底類別](../misc/virtual-base-classes.md)  
  
-   [虛擬函式](../cpp/virtual-functions.md)  
  
-   [明確覆寫](../cpp/explicit-overrides-cpp.md)  
  
-   [抽象類別](../cpp/abstract-classes-cpp.md)  
  
-   [範圍規則的摘要](../cpp/summary-of-scope-rules.md)  
  
 本節中記載了 [\_\_super](../cpp/super.md) 和 [\_\_interface](../cpp/interface.md) 關鍵字。  
  
## 請參閱  
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)