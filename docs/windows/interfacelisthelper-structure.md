---
title: "InterfaceListHelper 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceListHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InterfaceListHelper 結構"
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceListHelper 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### 參數  
 `T0`  
 範本參數是 0，是需要的。  
  
 `T1`  
 範本參數是 1，依預設是未指定的。  
  
 `T2`  
 範本參數是 2，依預設是未指定的。第三個樣板參數。  
  
 `T3`  
 範本參數是 3，依預設是未指定的。  
  
 `T4`  
 範本參數是 4，依預設是未指定的。  
  
 `T5`  
 範本參數是 5，依預設是未指定的。  
  
 `T6`  
 範本參數是 6，依預設是未指定的。  
  
 `T7`  
 範本參數是 7，依預設是未指定的。  
  
 `T8`  
 範本參數是 8，依預設是未指定的。  
  
 `T9`  
 範本參數是 9，依預設是未指定的。  
  
## 備註  
 透過遞迴套用指定的樣板參數引數建立 InterfaceList 型別。  
  
 InterfaceListHelper 範本使用樣板參數 `T0` 定義 InterfaceList 結構中第一個資料成員，然後以遞迴方式套用 InterfaceListHelper 樣板與其餘的樣板參數。  在沒有其他範本參數， InterfaceListHelper 停止。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`TypeT`|型別 InterfaceList 的同義字。|  
  
## 繼承階層架構  
 `InterfaceListHelper`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)