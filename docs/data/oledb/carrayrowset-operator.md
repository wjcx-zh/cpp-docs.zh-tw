---
title: "CArrayRowset::operator | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArrayRowset::operator[]"
  - "CArrayRowset.operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算子 [], 陣列"
  - "[] 運算子"
  - "operator[], 陣列"
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArrayRowset::operator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供在資料列集中存取資料列、類似陣列的語法。  
  
## 語法  
  
```  
  
      TAccessor  
      & operator[](int nRow);  
```  
  
#### 參數  
 `TAccessor`  
 指定儲存在資料列集中存取子型別的範本參數。  
  
 `nRow`  
 \[in\] 要存取的行數 \(陣列項目\)。  
  
## 傳回值  
 要求的資料列內容。  
  
## 備註  
 如果 `nRow` 超出資料列集的資料列數，就會擲回例外狀況。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CArrayRowset 類別](../../data/oledb/carrayrowset-class.md)