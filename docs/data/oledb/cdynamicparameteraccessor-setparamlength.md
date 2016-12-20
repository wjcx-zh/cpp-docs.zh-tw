---
title: "CDynamicParameterAccessor::SetParamLength | Microsoft Docs"
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
  - "ATL::CDynamicParameterAccessor::SetParamLength"
  - "CDynamicParameterAccessor.SetParamLength"
  - "ATL.CDynamicParameterAccessor.SetParamLength"
  - "CDynamicParameterAccessor::SetParamLength"
  - "SetParamLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamLength 方法"
ms.assetid: d8e0bbfe-e1ae-4a8f-9567-584fbb0c8385
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::SetParamLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定在緩衝區中的指定參數的長度。  
  
## 語法  
  
```  
  
      bool SetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH length  
);  
```  
  
#### 參數  
 `nParam`  
 \[參數的數目 \(從 1\) 的位移。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  為請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。  
  
 *length*  
 \[長度在指定參數的位元組。  
  
## 備註  
 在成功傳回 **true** 和 **false** 發生錯誤。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)