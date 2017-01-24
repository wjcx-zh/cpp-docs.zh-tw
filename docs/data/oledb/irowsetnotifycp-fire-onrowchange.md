---
title: "IRowsetNotifyCP::Fire_OnRowChange | Microsoft Docs"
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
  - "IRowsetNotifyCP.Fire_OnRowChange"
  - "ATL.IRowsetNotifyCP.Fire_OnRowChange"
  - "Fire_OnRowChange"
  - "ATL::IRowsetNotifyCP::Fire_OnRowChange"
  - "IRowsetNotifyCP::Fire_OnRowChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnRowChange 方法"
ms.assetid: 6f9beed6-7a69-4c92-936f-422e98f3de5c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyCP::Fire_OnRowChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

廣播 [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) 事件至連接點 **IID\_IRowsetNotify** 上所有的接聽程式，通知消費者有影響整個資料列的變更。  
  
## 語法  
  
```  
  
      HRESULT Fire_OnRowChange(  
   IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考資訊* 中的 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)