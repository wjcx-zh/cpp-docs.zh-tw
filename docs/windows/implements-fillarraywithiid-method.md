---
title: "Implements::FillArrayWithIid 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Implements::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implements::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

插入目前第零個樣板參數的介面 ID 至指定的陣列元素。  
  
## 語法  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### 參數  
 `index`  
 指出這個作業開始的陣列元素之以零起始的索引。  當這個作業完成時，`index` 增加 1。  
  
 `iids`  
 型別為 IID 的陣列。  
  
## 備註  
 內部 Helper 函式。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Implements 結構](../windows/implements-structure.md)