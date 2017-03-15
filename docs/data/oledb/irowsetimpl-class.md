---
title: "IRowsetImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetImpl 類別"
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IRowset` 介面的實作。  
  
## 語法  
  
```  
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*   
   >  
>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IRowsetImpl` 。  
  
 `RowsetInterface`  
 衍生自 `IRowsetImpl` 的類別。  
  
 `RowClass`  
 **HROW** 的儲存單位。  
  
 `MapClass`  
 由提供者保留的所有資料列控制代碼的儲存單位。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|將參考次數 \(Reference Count\) 加入至現有的資料列控制代碼。|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|被[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 呼叫以配置新的 **HROW**。  不會直接由使用者呼叫。|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|從資料列集的資料列複本擷取資料。|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|傳回指定欄位的狀態。|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|循序擷取資料列，並且會記住上一個位置。|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|建構函式。  不會直接由使用者呼叫。|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|被[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) 和 [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)呼叫。  不會直接由使用者呼叫。|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|釋放資料列。|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|當資料列集先建立時，變更位置下擷取位置設定至其初始位置；也就是它的位置時。|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|設定指定之欄位的狀態旗標。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|指出提供者是否支援向後擷取。|  
|[m\_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|指出提供者是否可以將自己的游標反向移動。|  
|[m\_bReset](../../data/oledb/irowsetimpl-m-breset.md)|指出提供者是否重設其游標位置。  在 [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)反向移動或向後擷取有特殊的意義。|  
|[m\_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|一個對行集合的索引代表游標。|  
|[m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|資料列控制代碼的清單。|  
  
## 備註  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) 是基礎資料列集介面。  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)