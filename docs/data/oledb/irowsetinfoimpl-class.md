---
title: "IRowsetInfoImpl 類別 | Microsoft Docs"
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
  - "ATL.IRowsetInfoImpl"
  - "IRowsetInfoImpl"
  - "ATL::IRowsetInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetInfoImpl 類別"
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetInfoImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)介面的實作。  
  
## 語法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IRowsetInfoImpl` 。  
  
 `PropClass`  
 該使用者可定義的屬性類別會預設值為 `T`。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|傳回資料列集 \(Rowset\) 支援之所有屬性的目前設定。|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|傳回資料列集的介面指標，這個資料列集即為要套用書籤的資料列集。|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|傳回建立此資料列集之物件 \(命令或工作階段\) 上的介面指標。|  
  
## 備註  
 在資料列集的強制介面。  這個類別會實作在您的命令類別使用 [屬性集對應](../../data/oledb/begin-propset-map.md) 定義資料列集屬性。  雖然資料列集類別的 .NET 命令類別屬性集合，資料列集提供執行階段屬性本身的複本，，因為命令或工作階段物件時建立。  
  
## 需求  
 **Header:** altdb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)