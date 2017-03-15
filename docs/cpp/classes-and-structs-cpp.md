---
title: "類別和結構 (C++) | Microsoft Docs"
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
  - "類別 [C++]"
  - "結構的比較, C++ 類別"
  - "使用者定義類型"
  - "使用者定義類型, C++ 類別"
  - "Visual C++, 類別"
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類別和結構 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節介紹 C\+\+ 類別和結構。  這兩個建構在 C\+\+ 中相同，差異在於結構中的預設存取範圍是公用，而類別中的預設值是私用。  
  
```  
  
```  
  
 類別和結構是可讓您定義專屬類型的建構。  類別和結構可以同時包含資料成員和成員函式，以讓您描述類型的狀態和行為。  
  
 其中包含下列主題：  
  
-   [class](../cpp/class-cpp.md)  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [類別成員概觀](../cpp/class-member-overview.md)  
  
-   [成員存取控制](../cpp/member-access-control-cpp.md)  
  
-   [繼承](../cpp/inheritance-cpp.md)  
  
-   [靜態成員](../cpp/static-members-cpp.md)  
  
-   [轉換](../cpp/user-defined-type-conversions-cpp.md)  
  
-   [可變動的資料成員 \(mutable 規範\)](../cpp/mutable-data-members-cpp.md)  
  
-   [巢狀類別宣告](../cpp/nested-class-declarations.md)  
  
-   [匿名類別類型](../cpp/anonymous-class-types.md)  
  
-   [成員的指標](../cpp/pointers-to-members.md)  
  
-   [this 指標](../cpp/this-pointer.md)  
  
-   [C\+\+ 位元欄位](../cpp/cpp-bit-fields.md)  
  
 三個類別類型是結構、類別和等位。  它們是使用 [struct](../cpp/struct-cpp.md)、[class](../cpp/class-cpp.md) 和 [union](../cpp/unions.md) 關鍵字所宣告 \(請參閱[定義類別類型](http://msdn.microsoft.com/zh-tw/e8c65425-0f3a-4dca-afc2-418c3b1e57da)\)。  下表顯示這三個類別類型的差異。  
  
 如需等位的詳細資訊，請參閱[等位](../cpp/unions.md)。  如需 Managed 類別和結構的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
### 結構、類別和等位的存取控制和條件約束  
  
|結構|類別|等位|  
|--------|--------|--------|  
|類別索引鍵是 `struct`|類別索引鍵是 **class**|類別索引鍵是 **union**|  
|預設存取權是 public|預設存取權是 private|預設存取權是 public|  
|沒有使用條件約束|沒有使用條件約束|一次只使用一個成員|  
  
## 請參閱  
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)