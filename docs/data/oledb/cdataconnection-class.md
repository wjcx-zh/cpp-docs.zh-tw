---
title: "CDataConnection 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataConnection"
  - "ATL.CDataConnection"
  - "CDataConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataConnection 類別"
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDataConnection 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理與資料來源的連接。  
  
## 語法  
  
```  
class CDataConnection  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|建構函式。  執行個體化及初始化 `CDataConnection` 物件。|  
|[複製](../../data/oledb/cdataconnection-copy.md)|建立現有資料連接的複本。|  
|[開啟](../../data/oledb/cdataconnection-open.md)|使用初始化字串，開啟與資料來源的連接。|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|開始在目前連接的新工作階段。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 BOOL](../../data/oledb/cdataconnection-operator-bool.md)|判斷目前工作階段是否已在執行。|  
|[運算子 bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|判斷目前工作階段是否已在執行。|  
|[operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|傳回已包含之 `CDataSource` 物件的參考。|  
|[operator CDataSource\*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|傳回 `CDataSource` 物件的指標。|  
|[operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)|傳回已包含之 `CSession` 物件的參考。|  
|[operator CSession\*](../../data/oledb/cdataconnection-operator-csession-star.md)|傳回 `CSession` 物件的指標。|  
  
## 備註  
 `CDataConnection` 是建立用戶端一個有用的類別，因為它封裝必要的必須完成，連接到資料來源的物件 \(資料來源和工作階段\) 和某些工作  
  
 沒有 `CDataConnection`，您必須建立 `CDataSource` 物件，會呼叫 [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) 方法，然後建立 [CSession](../../data/oledb/csession-class.md) 物件的執行個體，呼叫物件的 [開啟](../../data/oledb/csession-open.md) 方法，然後建立 [CCommand](../../data/oledb/ccommand-class.md) 物件和呼叫其 **Open**\*方法。  
  
 `CDataConnection`，您需要建立連接物件，只將初始化字串，然後使用開啟命令的連接。  如果您在重複使用規劃與資料庫的連接，最好能保持連接開啟，因此， `CDataConnection` 提供便利的方式來進行。  
  
> [!NOTE]
>  如果您建立需要處理多個工作階段的資料庫應用程式，您必須使用 [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)