---
title: "CDynamicParameterAccessor::GetParamType | Microsoft Docs"
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
  - "CDynamicParameterAccessor.GetParamType"
  - "CDynamicParameterAccessor:GetParamType"
  - "CDynamicParameterAccessor::GetParamType"
  - "ATL.CDynamicParameterAccessor.GetParamType"
  - "GetParamType"
  - "ATL::CDynamicParameterAccessor::GetParamType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamType 方法"
ms.assetid: d9c46775-c2a6-4100-8b69-99f13c52958b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定之參數的資料型別。  
  
## 語法  
  
```  
  
      bool GetParamType(  
   DBORDINAL nParam,  
   DBTYPE* pType   
) const throw( );  
```  
  
#### 參數  
 `nParam`  
 \[參數的數目 \(從 1\) 的位移。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  為請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。  
  
 `pType`  
 \[out 包含指定參數的資料型別之變數的指標。  
  
## 傳回值  
 在成功傳回 **true** 和 **false** 發生錯誤。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)