---
title: "BoolStruct 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::BoolStruct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BoolStruct 結構"
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# BoolStruct 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
struct BoolStruct;  
```  
  
## 備註  
 BoolStruct 結構定義 ComPtr 是否處理介面的物件存留期 \(Lifetime\)。  [BoolType \(\)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) 運算子在內部使用 BoolStruct。  
  
## Members  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[BoolStruct::Member 資料成員](../windows/boolstruct-member-data-member.md)|指定 [ComPtr](../windows/comptr-class.md) 是，或者不是，處理介面的物件存留期 \(Lifetime\)。|  
  
## 繼承階層架構  
 `BoolStruct`  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType 運算子](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)