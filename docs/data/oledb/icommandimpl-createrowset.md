---
title: "ICommandImpl::CreateRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl::CreateRowset"
  - "ICommandImpl.CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset 方法"
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ICommandImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [執行](../../data/oledb/icommandimpl-execute.md) 建立單一資料列集。  
  
## 語法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### 參數  
 `RowsetClass`  
 表示使用者的資料列集類別的樣板類別 \(Template\-Class\) 成員。  通常由精靈產生。  
  
 `pUnkOuter`  
 \[in\] 控制 **IUnknown** 介面之指標做為彙總的一部分，因此，如果資料列集建立;否則，它會是空的。  
  
 `riid`  
 \[in\]對應至 `ICommand::Execute`的 `riid` 。  
  
 `pParams`  
 \[in\/out\] 對應至 `ICommand::Execute`的 `pParams` 。  
  
 `pcRowsAffected`  
 與 `pcRowsAffected` 對應於 `ICommand::Execute`。  
  
 `ppRowset`  
 \[in\/out\] 對應至 `ICommand::Execute`的 `ppRowset` 。  
  
 `pRowsetObj`  
 \[資料列集物件的指標。  一般而言不會使用這個參數，不過，當您必須在傳遞至 COM 物件之前對結構描述資料列集進行更多工作時可以使用它。  `pRowsetObj` 的存留期由 `ppRowset` 約束。  
  
## 傳回值  
 標準 `HRESULT` 值。  如需典型值的清單，請參閱 `ICommand::Execute` 。  
  
## 備註  
 若要建立多個資料列集，或是為建立不同的資料列集提供您的情況，進行不同的呼叫 `CreateRowset` 從 **Execute**。  
  
 請參閱 *OLE DB 程式設計人員參考* 中的 [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) 。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)