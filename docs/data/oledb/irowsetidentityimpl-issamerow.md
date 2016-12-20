---
title: "IRowsetIdentityImpl::IsSameRow | Microsoft Docs"
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
  - "IsSameRow"
  - "IRowsetIdentityImpl.IsSameRow"
  - "ATL.IRowsetIdentityImpl.IsSameRow"
  - "IRowsetIdentityImpl::IsSameRow"
  - "ATL::IRowsetIdentityImpl::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow 方法"
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetIdentityImpl::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較兩個資料列控制代碼查看它們是否參考相同的資料列。  
  
## 語法  
  
```  
  
      STDMETHOD( IsSameRow )(  
   HROW hThisRow,  
   HROW hThatRow   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) 。  
  
## 備註  
 要比較的控制代碼，這個方法轉換為 **HROW** 控制代碼給 **RowClass** 成員並在指標的 `memcmp` 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetIdentityImpl 類別](../../data/oledb/irowsetidentityimpl-class.md)