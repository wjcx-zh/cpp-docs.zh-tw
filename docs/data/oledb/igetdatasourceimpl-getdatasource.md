---
title: "IGetDataSourceImpl::GetDataSource | Microsoft Docs"
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
  - "GetDataSource"
  - "IGetDataSourceImpl.GetDataSource"
  - "IGetDataSourceImpl::GetDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDataSource 方法"
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IGetDataSourceImpl::GetDataSource
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回在建立此工作階段的資料來源物件的介面指標。  
  
## 語法  
  
```  
  
      STDMETHOD(GetDataSource)(   
   REFIID riid,   
   IUnknown ** ppDataSource    
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx) 。  
  
## 備註  
 有用，如果您需要存取資料來源物件中的屬性。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IGetDataSourceImpl 類別](../../data/oledb/igetdatasourceimpl-class.md)