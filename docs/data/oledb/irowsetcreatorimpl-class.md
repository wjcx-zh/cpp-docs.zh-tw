---
title: "IRowsetCreatorImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetCreatorImpl"
  - "ATL.IRowsetCreatorImpl"
  - "ATL::IRowsetCreatorImpl<T>"
  - "ATL.IRowsetCreatorImpl<T>"
  - "IRowsetCreatorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetCreatorImpl 類別"
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetCreatorImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行函式和 `IObjectWithSite` ，而且啟用 OLE DB 屬性 **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**。  
  
## 語法  
  
```  
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### 參數  
 `T`  
 衍生自 **IRowsetCreator** 類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|設定包含資料列集物件的網站。|  
  
## 備註  
 這個類別會從 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 繼承並覆寫 [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  當提供者命令或工作階段物件建立資料列時，它會在搜尋 `IObjectWithSite` 的資料列集物件的 `QueryInterface` 和呼叫會將資料列集物件的 **IUnkown** 介面的 `SetSite` 做為網站介面。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)