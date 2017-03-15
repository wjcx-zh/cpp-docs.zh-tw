---
title: "CDataSource::OpenFromInitializationString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource.OpenFromInitializationString"
  - "OpenFromInitializationString"
  - "CDataSource::OpenFromInitializationString"
  - "ATL::CDataSource::OpenFromInitializationString"
  - "ATL.CDataSource.OpenFromInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromInitializationString 方法"
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDataSource::OpenFromInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟使用者提供的字串初始化指定的資料來源。  
  
## 語法  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### 參數  
 *szInitializationString*  
 \[in\]初始化字串。  
  
 *fPromptForInfo*  
 \[in\]，如果這個引數設為 **true**，則 `OpenFromInitializationString` 會設定 **DBPROP\_INIT\_PROMPT** 屬性為 **DBPROMPT\_COMPLETEREQUIRED**，指定只有當需要詳細資訊時提示使用者。  這會初始化字串指定資料庫需要密碼的情況下很有用，不過，字串不包含密碼。  系統會提示使用者輸入密碼 \(或其他遺漏資訊\)，當嘗試連接到資料庫時。  
  
 預設值為 **false**，指定永不提示使用者 \(如將 **DBPROMPT\_NOPROMPT**設定為 **DBPROP\_INIT\_PROMPT** \)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法使用在 oledb32.dll 的 Service 元件開啟資料來源物件；這個 DLL 包含 Service 元件功能的實作 \(例如資源共用、自動交易登記等等\)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)