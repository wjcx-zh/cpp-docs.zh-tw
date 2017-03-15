---
title: "CDynamicParameterAccessor::GetParamName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::GetParamName"
  - "ATL.CDynamicParameterAccessor.GetParamName"
  - "GetParamName"
  - "CDynamicParameterAccessor.GetParamName"
  - "ATL::CDynamicParameterAccessor::GetParamName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamName 方法"
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::GetParamName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定之參數的名稱。  
  
## 語法  
  
```  
  
      LPOLESTR GetParamName(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### 參數  
 `nParam`  
 \[in\] 參數的數目 \(從 1 開始位移\)。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
## 傳回值  
 指定之參數的名稱。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)