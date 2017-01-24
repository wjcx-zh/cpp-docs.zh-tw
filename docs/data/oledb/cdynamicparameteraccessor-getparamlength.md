---
title: "CDynamicParameterAccessor::GetParamLength | Microsoft Docs"
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
  - "ATL::CDynamicParameterAccessor::GetParamLength"
  - "ATL.CDynamicParameterAccessor.GetParamLength"
  - "CDynamicParameterAccessor.GetParamLength"
  - "CDynamicParameterAccessor::GetParamLength"
  - "GetParamLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamLength 方法"
ms.assetid: 04d76931-911a-4915-9c2c-ad585a9f3854
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取在緩衝區中的指定參數的長度。  
  
## 語法  
  
```  
  
      bool GetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH* pLength  
);  
DBLENGTH* GetParamLength(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### 參數  
 `nParam`  
 \[in\] 參數的數目 \(從 1 開始位移\)。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pLength`  
 \[out\] 包含長度之變數的指標位於指定參數的位元組。  
  
## 備註  
 第一個覆寫會在成功回傳 **true** 或在失敗回傳 **false** 。  包含參數的長度的記憶體的第二個覆寫點。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)