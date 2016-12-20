---
title: "CDataSource::OpenFromFileName | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::OpenFromFileName"
  - "ATL::CDataSource::OpenFromFileName"
  - "OpenFromFileName"
  - "CDataSource.OpenFromFileName"
  - "ATL.CDataSource.OpenFromFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromFileName 方法"
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::OpenFromFileName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從以使用者提供的檔名指定的檔案，開啟資料來源。  
  
## 語法  
  
```  
  
        HRESULT OpenFromFileName(   
   LPCOLESTR szFileName    
) throw( );  
```  
  
#### 參數  
 `szFileName`  
 \[in\] 檔案的名稱，通常是資料來源連接 \(.UDL\) 檔案。  
  
 如需資料連結檔 \(.udl 檔案\) 的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的[資料連結 API 概觀](https://msdn.microsoft.com/en-us/library/ms718102.aspx)。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》中的＜OLE DB 服務＞：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)