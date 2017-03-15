---
title: "IRowsetIdentityImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetIdentityImpl"
  - "ATL.IRowsetIdentityImpl"
  - "IRowsetIdentityImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetIdentityImpl 類別"
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetIdentityImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 OLE DB [IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx) 介面，以啟用資料行識別的測試。  
  
## 語法  
  
```  
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
#### 參數  
 `T`  
 衍生自 `IRowsetIdentityImpl` 的類別。  
  
 `RowClass`  
 **HROW** 的儲存單位。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[IsSameRow](../../data/oledb/irowsetidentityimpl-issamerow.md)|比較兩個資料列控制代碼，以查看它們是否參考相同的資料列。|  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)