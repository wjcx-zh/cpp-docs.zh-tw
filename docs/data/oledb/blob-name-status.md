---
title: "BLOB_NAME_STATUS | Microsoft Docs"
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
  - "BLOB_NAME_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME_STATUS 巨集"
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_NAME_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

和 `BEGIN_COLUMN_MAP` 及 `END_COLUMN_MAP` 一同使用，以繫結二進位大型物件 \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\)。  與 [BLOB\_NAME](../../data/oledb/blob-name.md) 類似，但是這個巨集也會取得 BLOB 資料行的狀態。  
  
## 語法  
  
```  
  
BLOB_NAME_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
, status )  
```  
  
#### 參數  
 `pszName`  
 \[in\] 指向資料欄名稱之指標。  名稱必須是 Unicode 字串。  您可以在名稱前加上一個「L」表示結束，例如： `L"MyColumn"`。  
  
 *IID*  
 \[in\] 介面 GUID \(例如 **IDD\_ISequentialStream**\)，用來擷取 BLOB。  
  
 `flags`  
 \[in\] 如 OLE 結構化儲存體模型 \(例如 **STGM\_READ**\) 所定義的儲存模式旗標。  
  
 `data`  
 \[in\] 使用者資料記錄中對應的資料成員。  
  
 *status*  
 \[out\] BLOB 欄位的狀態。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_NAME](../../data/oledb/blob-name.md)   
 [BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)