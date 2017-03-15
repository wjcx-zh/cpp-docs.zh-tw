---
title: "CAccessor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CAccessor<T>"
  - "ATL::CAccessor"
  - "CAccessor"
  - "ATL::CAccessor<T>"
  - "ATL.CAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessor 類別"
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示其中一個存取子型別。  
  
## 語法  
  
```  
  
      template < class   
      T  
       >  
class CAccessor : public CAccessorBase, public T  
```  
  
#### 參數  
 `T`  
 使用者資料錄類別。  
  
## 備註  
 同時，請記錄以靜態方式繫結至資料來源時，請使用。  這個記錄包含緩衝區。  這個類別支援資料列集的多重存取子。  
  
 當您知道結構和資料庫的型別時，請使用這個存取子型別。  
  
 如果您的存取子包含指向必須釋放的記憶體的欄位 \(例如 `BSTR` \) 或介面，請呼叫 [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) 成員函式，在下一個讀取資料錄之前。  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)