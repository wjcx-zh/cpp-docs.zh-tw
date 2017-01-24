---
title: "IRowsetImpl::RestartPosition | Microsoft Docs"
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
  - "ATL.IRowsetImpl.RestartPosition"
  - "IRowsetImpl::RestartPosition"
  - "RestartPosition"
  - "ATL::IRowsetImpl::RestartPosition"
  - "IRowsetImpl.RestartPosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RestartPosition 方法"
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::RestartPosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當資料列集先建立時，變更位置下擷取位置設定至其初始位置；也就是它的位置時。  
  
## 語法  
  
```  
  
      STDMETHOD( RestartPosition )(  
   HCHAPTER /* hReserved */   
);  
```  
  
#### 參數  
 請參閱  *OLE DB 程式設計人員參考* 中的 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)。  
  
## 備註  
 資料列集的位置是 undefined，直到 **GetNextRow** 呼叫。  您可以 rowet 便會呼叫 [RestartPosition](#vcrefirowsetimplrestartposition) 然後擷取或反向移動。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)