---
title: "CEnumeratorAccessor 類別 | Microsoft Docs"
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
  - "ATL::CEnumeratorAccessor"
  - "CEnumeratorAccessor"
  - "ATL.CEnumeratorAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumeratorAccessor 類別"
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEnumeratorAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由 [CEnumerator](../../data/oledb/cenumerator-class.md) 用來列舉資料存取資料。  
  
## 語法  
  
```  
class CEnumeratorAccessor  
```  
  
## 成員  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|表示列舉值是否是父列舉程式的變數，如果資料行為列舉值。|  
|[m\_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|指出資料變數描述資料來源或列舉值。|  
|[m\_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|資料來源或列舉值的描述。|  
|[m\_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|列舉程式和資料來源的名稱。|  
|[m\_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|用來傳遞給 [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) 的字串，可得到資料來源或列舉值的 Moniker。|  
  
## 備註  
 此資料列集包括資料來源和列舉值顯示從目前的列舉值。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)