---
title: "CDynamicParameterAccessor::GetParamStatus | Microsoft Docs"
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
  - "CDynamicParameterAccessor::GetParamStatus"
  - "CDynamicParameterAccessor.GetParamStatus"
  - "ATL.CDynamicParameterAccessor.GetParamStatus"
  - "ATL::CDynamicParameterAccessor::GetParamStatus"
  - "GetParamStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamStatus 方法"
ms.assetid: 9300225a-616c-4a7d-82d0-8c2ecd4d8185
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取在緩衝區中的指定參數的狀態。  
  
## 語法  
  
```  
  
      bool GetParamStatus(  
   DBORDINAL nParam,  
   DBSTATUS* pStatus  
);  
DBSTATUS* GetParamStatus(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### 參數  
 `nParam`  
 \[in\] 參數的數目 \(從 1 開始位移\)。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pStatus`  
 \[out\] 包含指定之參數的 `DBSTATUS` 狀態的變數的指標。  如需 `DBSTATUS` 值的詳細資訊，請參閱《 *OLE DB 程式設計人員參考》的*[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或搜尋 oledb.h 的 `DBSTATUS` 。  
  
## 備註  
 第一個覆寫會在成功回傳 **true** 或在失敗回傳 **false** 。  包含指定參數的位置的記憶體的第二個覆寫點。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)