---
title: "CDynamicParameterAccessor::GetParam | Microsoft Docs"
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
  - "CDynamicParameterAccessor::GetParam"
  - "ATL.CDynamicParameterAccessor.GetParam"
  - "CDynamicParameterAccessor::GetParam<ctype>"
  - "CDynamicParameterAccessor.GetParam"
  - "GetParam"
  - "ATL::CDynamicParameterAccessor::GetParam<ctype>"
  - "ATL::CDynamicParameterAccessor::GetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParam 方法"
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從參數緩衝區擷取非字串資料為指定的參數。  
  
## 語法  
  
```  
  
      template < class ctype > bool GetParam(   
   DBORDINAL nParam,   
   ctype* pData    
) const throw( );  
template < class ctype > bool GetParam(   
   TCHAR* pParamName,   
   ctype* pData    
) const throw( );  
void* GetParam(   
   DBORDINAL nParam    
) const throw( );  
void* GetParam(   
   TCHAR* pParamName    
) const throw( );  
```  
  
#### 參數  
 `ctype`  
 是資料型別的範本參數。  
  
 `nParam`  
 \[參數的數目 \(從 1\) 的位移。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pParamName`  
 \[in\] 參數名稱。  
  
 `pData`  
 \[out\] 包含資料的記憶體的指標擷取緩衝區。  
  
## 傳回值  
 對於 nontemplated 版本，其中包含資料的記憶體中的點要從緩衝區。  對於包含版本、傳回 **true** 在 **false** 在成功或失敗。  
  
 使用 `GetParam` 緩衝區擷取非字串參數資料。  使用 [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) 從緩衝區擷取字串參數資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)