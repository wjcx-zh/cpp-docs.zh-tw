---
title: "CDynamicAccessor::SetStatus | Microsoft Docs"
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
  - "CDynamicAccessor::SetStatus"
  - "ATL::CDynamicAccessor::SetStatus"
  - "CDynamicAccessor.SetStatus"
  - "ATL.CDynamicAccessor.SetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetStatus 方法"
ms.assetid: 6db82694-e87d-4bf8-a7e3-5765cf6abff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定指定欄位的狀態。  
  
## 語法  
  
```  
  
      bool SetStatus(   
   DBORDINAL nColumn,   
   DBSTATUS status    
) throw( );  
bool SetStatus(   
   const CHAR* pColumnName,   
   DBSTATUS status    
) throw( );  
bool SetStatus(   
   const WCHAR* pColumnName,   
   DBSTATUS status    
) throw( );  
```  
  
#### 參數  
 `nColumn`  
 \[in\]資料行編號。  資料行編號從 1 開始。  一個為 0 的值表示書籤資料行 \(如果有的話\)。  
  
 *status*  
 \[in\] 欄位狀態：  如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)。  
  
 `pColumnName`  
 \[in\] 指向包含資料行名稱的字串之指標。  
  
## 傳回值  
 如果指定的資料行狀態成功，將傳回 **true** 。  否則，函式會傳回**false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)