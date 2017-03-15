---
title: "pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pair 類別 [STL/CLR]"
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述封裝一對值的物件。  
  
## 語法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### 參數  
 Value1  
 第一個包裝值的型別。  
  
 Value2  
 第二個包裝值的型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[pair::first\_type](../dotnet/pair-first-type-stl-clr.md)|第一個包裝值的型別。|  
|[pair::second\_type](../dotnet/pair-second-type-stl-clr.md)|第二個包裝值的型別。|  
  
|成員物件|說明|  
|----------|--------|  
|[pair::first](../dotnet/pair-first-stl-clr.md)|第一個儲存值。|  
|[pair::second](../dotnet/pair-second-stl-clr.md)|第二個儲存值。|  
  
|成員函式|說明|  
|----------|--------|  
|[pair::pair](../dotnet/pair-pair-stl-clr.md)|建構一對物件。|  
|[pair::swap](../dotnet/pair-swap-stl-clr.md)|交換兩對的內容。|  
  
|運算子|說明|  
|---------|--------|  
|[pair::operator\=](../dotnet/pair-operator-assign-stl-clr.md)|取代儲存的一對值。|  
  
## 備註  
 儲存一對值的物件。  您可以使用這個樣本類別將兩個值合併為單一物件。  請注意 `cliext::pair` \(此處描述的\) 只儲存 Managed 型別；若要儲存一對 Unmanaged 型別，請使用 `<utility>` 中宣告的 `std::pair`。  
  
## 需求  
 **標頭 ：** \<cliext\/utility\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [make\_pair](../dotnet/make-pair-stl-clr.md)