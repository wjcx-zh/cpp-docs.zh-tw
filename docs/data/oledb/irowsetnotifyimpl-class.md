---
title: "IRowsetNotifyImpl 類別 | Microsoft Docs"
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
  - "ATL.IRowsetNotifyImpl"
  - "ATL::IRowsetNotifyImpl"
  - "IRowsetNotifyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyImpl 類別"
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作和暫存器在消費者 \(也稱為接收」\) [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) ，以便處理通知。  
  
## 語法  
  
```  
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|告知消費者，資料行值的任何變更。|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|告知消費者，資料列的第一個變更或影響整個資料列的任何變更。|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|告知消費者，影響整個資料列集的任何變更。|  
  
## 備註  
 如需實作連接點的 [接收通知](../../data/oledb/receiving-notifications.md) 連接在消費者。  
  
 `IRowsetNotifyImpl` 為 `IRowsetNotify`的空的實作，以 `IRowsetNotify` 方法的 [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)、 [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)和 [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)空函式。  如果您從這個類別繼承，當您實作 `IRowsetNotify` 介面時，您可以實作需要的方法。  您也必須為其他方法提供空的實作。  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)