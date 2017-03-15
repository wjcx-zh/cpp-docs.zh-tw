---
title: "CRestrictions 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRestrictions"
  - "CRestrictions"
  - "ATL.CRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRestrictions 類別"
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CRestrictions 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您指定結構描述資料列集指定限制的泛型類別。  
  
## 語法  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### 參數  
 `T`  
 用於存取子的類別。  
  
 `nRestrictions`  
 結構描述資料列集的限制資料行數目。  
  
 `pguid`  
 指向結構描述的 GUID 的指標。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[開啟](../../data/oledb/crestrictions-open.md)|傳回根據使用者提供的限制設定的結果。|  
  
## 需求  
 **標頭：** atldbsch.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)