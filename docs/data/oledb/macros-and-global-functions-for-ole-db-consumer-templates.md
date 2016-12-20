---
title: "OLE DB 消費者樣板的巨集和全域函式 | Microsoft Docs"
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
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "巨集, OLE DB 消費者樣板"
  - "OLE DB 消費者樣板, 巨集"
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 消費者樣板的巨集和全域函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 消費者樣板包括下列巨集和全域函式:  
  
### 全域函式  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|如果傳回錯誤，傾印 OLE DB 錯誤記錄資訊傾印至裝置。|  
  
### 存取子對應巨集  
  
|||  
|-|-|  
|[BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)|存取子標記項目的開頭。|  
|[BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)|標記存取程序對應項目的開頭。|  
|[END\_ACCESSOR](../../data/oledb/end-accessor.md)|存取子標記項目的結尾。|  
|[END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)|標記存取程序對應項目的結尾。|  
  
### 資料行對應巨集  
  
|||  
|-|-|  
|[BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)|資料行對應項目的開頭加入使用者資料錄類別的。|  
|[BLOB\_ENTRY](../../data/oledb/blob-entry.md)|用來繫結二進位大型物件 \(BLOB\)。|  
|[BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)|報告 BLOB 資料行的長度。|  
|[BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)|報告 BLOB 資料行的長度和狀態。|  
|[BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)|報告 BLOB 資料行的狀態。|  
|[BLOB\_NAME](../../data/oledb/blob-name.md)|由資料行名稱繫結二進位大型物件。|  
|[BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)|報告 BLOB 資料行的長度。|  
|[BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)|報告 BLOB 資料行的長度和狀態。|  
|[BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)|報告 BLOB 資料行的狀態。|  
|[BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)|表示資料列集的書籤項目。  書籤項目是一種特殊的資料行型別。|  
|[COLUMN\_ENTRY](../../data/oledb/column-entry.md)|表示繫結至資料庫中的特定資料行。|  
|[COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)|表示繫結至資料庫中的特定資料行。  支援 `type`、 *長度*、 *精確度*、 `scale`和 *狀態* 參數。|  
|[COLUMN\_ENTRY\_LENGTH](../../data/oledb/column-entry-length.md)|表示繫結至資料庫中的特定資料行。  支援 *長度* 變數。|  
|[COLUMN\_ENTRY\_LENGTH\_STATUS](../../data/oledb/column-entry-length-status.md)|表示繫結至資料庫中的特定資料行。  支援*狀態*和*長度*參數。|  
|[COLUMN\_ENTRY\_PS](../../data/oledb/column-entry-ps.md)|表示繫結至資料庫中的特定資料行。  支援 *精確度* 和 `scale` 參數。|  
|[COLUMN\_ENTRY\_PS\_LENGTH](../../data/oledb/column-entry-ps-length.md)|表示繫結至資料庫中的特定資料行。  支援 *長度* 變數、 *精確度* 和 `scale` 參數。|  
|[COLUMN\_ENTRY\_PS\_LENGTH\_STATUS](../../data/oledb/column-entry-ps-length-status.md)|表示繫結至資料庫中的特定資料行。  支援 *狀態* 和*長度*變數、*精確度*和 `scale` 參數。|  
|[COLUMN\_ENTRY\_PS\_STATUS](../../data/oledb/column-entry-ps-status.md)|表示繫結至資料庫中的特定資料行。  支援 *狀態* 變數、 *精確度* 和 `scale` 參數。|  
|[COLUMN\_ENTRY\_STATUS](../../data/oledb/column-entry-status.md)|表示繫結至資料庫中的特定資料行。  支援 *狀態* 變數。|  
|[COLUMN\_ENTRY\_TYPE](../../data/oledb/column-entry-type.md)|表示繫結至資料庫中的特定資料行。  支援 `type` 參數。|  
|[COLUMN\_ENTRY\_TYPE\_SIZE](../../data/oledb/column-entry-type-size.md)|表示繫結至資料庫中的特定資料行。  支援 `type` 和 `size` 參數。|  
|[COLUMN\_NAME](../../data/oledb/column-name.md)|用名字表示繫結至資料庫中的特定資料行。|  
|[COLUMN\_NAME\_EX](../../data/oledb/column-name-ex.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料型別、大小、精確度、小數點位數、資料行長度和資料列狀態的規格。|  
|[COLUMN\_NAME\_LENGTH](../../data/oledb/column-name-length.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料行長度的規格。|  
|[COLUMN\_NAME\_LENGTH\_STATUS](../../data/oledb/column-name-length-status.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料行長度和狀態的規格。|  
|[COLUMN\_NAME\_PS](../../data/oledb/column-name-ps.md)|用名字表示繫結至資料庫中的特定資料行。  支援的有效位數和小數位數的規格。|  
|[COLUMN\_NAME\_PS\_LENGTH](../../data/oledb/column-name-ps-length.md)|用名字表示繫結至資料庫中的特定資料行。  支援精確度、小數點位數和資料行長度的規格。|  
|[COLUMN\_NAME\_PS\_LENGTH\_STATUS](../../data/oledb/column-name-ps-length-status.md)|用名字表示繫結至資料庫中的特定資料行。  支援整數位數、小數位數、資料行長度和資料列狀態的規格。|  
|[COLUMN\_NAME\_PS\_STATUS](../../data/oledb/column-name-ps-status.md)|用名字表示繫結至資料庫中的特定資料行。  支援精確度、小數點位數和資料行狀態的規格。|  
|[COLUMN\_NAME\_STATUS](../../data/oledb/column-name-status.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料行狀態的規格。|  
|[COLUMN\_NAME\_TYPE](../../data/oledb/column-name-type.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料型別的規格。|  
|[COLUMN\_NAME\_TYPE\_PS](../../data/oledb/column-name-type-ps.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料型別、精確度和小數點位數的規格。|  
|[COLUMN\_NAME\_TYPE\_SIZE](../../data/oledb/column-name-type-size.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料型別和大小的規格。|  
|[COLUMN\_NAME\_TYPE\_STATUS](../../data/oledb/column-name-type-status.md)|用名字表示繫結至資料庫中的特定資料行。  支援資料型別和資料列狀態的規格。|  
|[END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)|標記列對應項目的結尾。|  
  
### 命令巨集  
  
|||  
|-|-|  
|[DEFINE\_COMMAND](../../data/oledb/define-command.md)|指定將用來建立資料列時， [CCommand](../../data/oledb/ccommand-class.md) 類別中的命令。  只接受字串輸入符合指定的應用程式類型 \(ANSI 或 Unicode\)。  建議您使用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) 取代 `DEFINE_COMMAND`。|  
|[DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md)|指定將用來建立資料列時， [CCommand](../../data/oledb/ccommand-class.md) 類別中的命令。  支援 ANSI 和 Unicode 應用程式。|  
  
### 參數對應巨集  
  
|||  
|-|-|  
|[BEGIN\_PARAM\_MAP](../../data/oledb/begin-param-map.md)|參數對應項目的開頭加入使用者資料錄類別的。|  
|[END\_PARAM\_MAP](../../data/oledb/end-param-map.md)|標記參數對應項目的結尾。|  
|[SET\_PARAM\_TYPE](../../data/oledb/set-param-type.md)|指定 `SET_PARAM_TYPE` 之後巨集做為輸入、輸出或輸入\/輸出的 `COLUMN_ENTRY` 巨集。|  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)