---
title: "CDynamicParameterAccessor::SetParamString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicParameterAccessor.SetParamString"
  - "ATL::CDynamicParameterAccessor::SetParamString"
  - "SetParamString"
  - "CDynamicParameterAccessor::SetParamString"
  - "CDynamicParameterAccessor.SetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamString 方法"
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::SetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定在緩衝區中的指定參數的字串資料。  
  
## 語法  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
```  
  
#### 參數  
 `nParam`  
 \[in\] 參數的數目 \(從 1 開始位移\)。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pString`  
 \[in\] ANSI \(**CHAR**\) 或 Unicode \(**WCHAR**\) 指定參數的字串資料之的指標。  請參閱在 oledb.h 的 `DBSTATUS` 。  
  
 *status*  
 \[in\] 指定之參數的 `DBSTATUS` 狀態。  如需 `DBSTATUS` 值的詳細資訊，請參閱《 *OLE DB 程式設計人員參考》的*[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或搜尋 oledb.h 的 `DBSTATUS` 。  
  
## 備註  
 如果成功則傳回 **true**，失敗則傳回 **false**。  
  
 如果您嘗試設定大於指定 `pString`的最大大小的字串，`SetParamString` 將會失敗。  
  
 使用 `SetParamString` 設定字串緩衝區的參數資料。  使用 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 將緩衝區的非字串參數資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)