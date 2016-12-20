---
title: "CDataSource::GetInitializationString | Microsoft Docs"
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
  - "ATL::CDataSource::GetInitializationString"
  - "CDataSource.GetInitializationString"
  - "GetInitializationString"
  - "CDataSource::GetInitializationString"
  - "ATL.CDataSource.GetInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInitializationString 方法"
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::GetInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取目前開啟資料來源初始化字串。  
  
## 語法  
  
```  
  
      HRESULT GetInitializationString(   
   BSTR* pInitializationString,   
   bool bIncludePassword = false    
) throw( );  
```  
  
#### 參數  
 *pInitializationString*  
 \[out\]初始化字串的指標。  
  
 *bIncludePassword*  
 \[ **true** ，如果字串包含密碼;否則 **false**。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 產生的初始化字串可用來後重新開啟這個資料來源的連接。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)