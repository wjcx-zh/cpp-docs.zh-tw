---
title: "IAccessorImpl 類別 | Microsoft Docs"
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
  - "IAccessorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAccessorImpl 類別"
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供[oledbIAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) 介面類別的實作。  
  
## 語法  
  
```  
template <  
   class T,   
   class BindType = ATLBINDINGS,   
   class BindingVector = CAtlMap <   
      HACCESSOR hAccessor,   
      BindType* pBindingsStructure   
   >   
>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### 參數  
 `T`  
 資料列集或命令物件類別。  
  
 `BindType`  
 儲存格為繫結資訊。  預設值為 **ATLBINDINGS** 結構 \(請參閱 atldb.h\)。  
  
 `BindingVector`  
 儲存格為資料行資訊。  預設值為主要項目是 **HACCESSOR** 值的 [CAtlMap](../../atl/reference/catlmap-class.md) ，而值項目是指向 `BindType` 結構。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|建構函式。|  
  
### 介面方法  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|將參考次數 \(Reference Count\) 加入至現有的存取子 \(Accessor\)。|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|透過一組繫結建立存取子。|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|傳回存取子中的繫結。|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|釋放存取子。|  
  
## 備註  
 這是必須在資料列集和命令。  OLE DB 需要提供者實作 **HACCESSOR**，是標記為陣列 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 結構。  `IAccessorImpl` 提供的**HACCESSOR**是 `BindType` 結構的位址。  根據預設， `BindType` 定義為 `IAccessorImpl` 樣板定義的 **ATLBINDINGS** 。  `BindType` 提供 `IAccessorImpl` 所使用的機制追蹤項目數其 **DBBINDING** 陣列以及參考計數和存取子旗標。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)