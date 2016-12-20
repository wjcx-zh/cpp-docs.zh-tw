---
title: "CRowset::GetData | Microsoft Docs"
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
  - "CRowset<TAccessor>::GetData"
  - "ATL::CRowset<TAccessor>::GetData"
  - "ATL::CRowset::GetData"
  - "ATL.CRowset<TAccessor>.GetData"
  - "CRowset<TAccessor>.GetData"
  - "CRowset::GetData"
  - "CRowset.GetData"
  - "ATL.CRowset.GetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetData 方法 [OLE DB]"
ms.assetid: 1e0347b5-3e24-4ff8-a790-839616c1522f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::GetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料列集的資料列複本擷取資料。  
  
## 語法  
  
```  
  
      HRESULT GetData( ) throw( );   
HRESULT GetData(   
   int nAccessor    
) throw( );  
```  
  
#### 參數  
 `nAccessor`  
 \[in\] 使用的存取子 \(零位移\) 索引編號來存取資料。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 如果您指定不在 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)的 autoaccessor 的存取子，請使用這個方法透過存取子數字明確取得資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)