---
title: "修改 RMyProviderRowset 的繼承 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "繼承 [C++]"
  - "RMyProviderRowset"
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 修改 RMyProviderRowset 的繼承
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要將 `IRowsetLocate` 介面加入至簡單唯讀提供者範例內，請修改 **RMyProviderRowset** 的繼承。  一開始，**RMyProviderRowset** 會繼承自 `CRowsetImpl`。  您需要將它修改為繼承自 **CRowsetBaseImpl**。  
  
 若要進行此步驟，請在 MyProviderRS.h 內建立新的 `CMyRowsetImpl` 類別：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate > >  
{  
...  
};  
```  
  
 現在，依照下列方式編輯 MyProviderRS.h 的 COM 介面對應：  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 這樣會建立一個 COM 介面對應，可用來通知 `CMyRowsetImpl` 為 `IRowset` 和 `IRowsetLocate` 兩個介面呼叫 **QueryInterface** 。  為了取得其他資料列集類別的所有實作，此對應會將 `CMyRowsetImpl` 類別連結回 OLE DB 樣板所定義的 **CRowsetBaseImpl** 類別；對應會使用 COM\_INTERFACE\_ENTRY\_CHAIN 巨集通知 OLE DB 樣板掃描 **CRowsetBaseImpl** 的 COM 對應，以回應 `QueryInterface` 呼叫。  
  
 最後，對應會依照下列方式，修改 `RAgentRowset` 成繼承自 `CMyRowsetImpl`，連結 `RAgentRowset` 到 `CMyRowsetBaseImpl`：  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` 現在可於運用其他的資料列集類別實作中，使用 `IRowsetLocate` 介面。  
  
 完成之後，您可[動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 請參閱  
 [增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)