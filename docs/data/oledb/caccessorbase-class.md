---
title: "CAccessorBase 類別 | Microsoft Docs"
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
  - "CAccessorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorBase 類別"
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 OLE DB 樣板中衍生自這個類別的任何存取子。  `CAccessorBase` 可讓一個資料列集處理多個存取子。  它也為參數和輸出行提供繫結。  
  
## 語法  
  
```  
// Replace with syntax  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/caccessorbase-close.md)|關閉存取子。|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|擷取存取子的控制代碼。|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|擷取類別建立的存取子數目。|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|測試指定的存取子是否為 autoaccessor。|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|釋放存取子。|  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)