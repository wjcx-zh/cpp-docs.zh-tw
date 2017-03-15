---
title: "HandleT::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 運算子"
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的 HandleT 物件中的值移動至目前 HandleT 物件。  
  
## 語法  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### 參數  
 `h`  
 對控制代碼的右值參考。  
  
## 傳回值  
 目前 HandleT 物件的參考。  
  
## 備註  
 這個作業會使參數 `h`所指定的 HandleT 物件無效。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)