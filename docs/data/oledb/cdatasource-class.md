---
title: "CDataSource 類別 | Microsoft Docs"
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
  - "ATL.CDataSource"
  - "ATL::CDataSource"
  - "CDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource 類別"
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會對應至 OLE DB 資料來源物件，傳遞代表提供者連接至資料來源。  
  
## 語法  
  
```  
class CDataSource  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/cdatasource-close.md)|關閉連接。|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|擷取目前開啟資料來源初始化字串。|  
|[GetProperties](../../data/oledb/cdatasource-getproperties.md)|取得用於連接資料來源目前設定的屬性值。|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|取得用於連接資料來源目前設定的單一屬性的值。|  
|[開啟](../../data/oledb/cdatasource-open.md)|建立與提供者 \(資料來源\) 的連接使用 **CLSID ProgID**，或者 `CEnumerator` 呼叫端提供的 Moniker。|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|開啟資料來源使用者提供的檔名指定的檔案。|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|開啟使用字串中指定的資料來源。|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|允許使用者選取先前建立的資料連結檔案開啟對應的資料來源。|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|使用資料連結內容對話方塊中，開啟資料來源物件。|  
  
## 備註  
 一或多個資料庫工作階段可為單一連接。  這些工作階段由 `CSession`表示。  您必須呼叫 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 在建立工作階段之前開啟連結的 `CSession::Open`。  
  
 如需 `CDataSource` 控制項的使用範例，請參閱[CatDB](../../top/visual-cpp-samples.md)範例。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)