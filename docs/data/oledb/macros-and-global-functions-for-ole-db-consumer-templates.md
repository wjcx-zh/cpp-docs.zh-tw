---
title: "巨集和全域函式的 OLE DB 消費者樣板 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755762e8b77cee9603074fdc8050d227fbd2eeb1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 消費者樣板的巨集和全域函式
OLE DB 消費者樣板可包括下列巨集和全域函式：  
  
### <a name="global-functions"></a>全域函式  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|如果傳回錯誤，傾印 OLE DB 錯誤記錄傾印裝置的資訊。|  
  
### <a name="accessor-map-macros"></a>存取子對應巨集  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|標記存取子項目的開頭。|  
|[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)|標記存取子對應項目的開頭。|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|標記存取子項目的結尾。|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|存取子對應項目結束標記。|  
  
### <a name="column-map-macros"></a>資料行對應巨集  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|標記資料行對應中的項目使用者記錄類別開頭。|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|用來繫結二進位大型物件 (BLOB)。|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|報告的 BLOB 資料行的長度。|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|報告的長度和狀態的 BLOB 資料行。|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|報告的 BLOB 資料行的狀態。|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|用來將二進位大型物件繫結資料行名稱。|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|報告的 BLOB 資料行的長度。|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|報告的長度和狀態的 BLOB 資料行。|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|報告的 BLOB 資料行的狀態。|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|代表從資料列集的書籤項目。 書籤項目是一種特殊的資料行項目。|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|表示在資料庫中的特定資料行的繫結。|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|表示在資料庫中的特定資料行的繫結。 支援`type`，*長度*，*精確度*， `scale`，和*狀態*參數。|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|表示在資料庫中的特定資料行的繫結。 支援*長度*變數。|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|表示在資料庫中的特定資料行的繫結。 支援*狀態*和*長度*參數。|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|表示在資料庫中的特定資料行的繫結。 支援*精確度*和`scale`參數。|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|表示在資料庫中的特定資料行的繫結。 支援*長度*變數*精確度*和`scale`參數。|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|表示在資料庫中的特定資料行的繫結。 支援*狀態*和*長度*變數*精確度*和`scale`參數。|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|表示在資料庫中的特定資料行的繫結。 支援*狀態*變數*精確度*和`scale`參數。|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|表示在資料庫中的特定資料行的繫結。 支援*狀態*變數。|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|表示在資料庫中的特定資料行的繫結。 支援`type`參數。|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|表示在資料庫中的特定資料行的繫結。 支援`type`和`size`參數。|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|表示繫結至資料庫中的特定資料行的名稱。|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型、 大小、 有效位數、 小數位數、 資料行長度，以及資料行狀態的規格。|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|表示繫結至資料庫中的特定資料行的名稱。 支援資料行長度的規格。|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料行長度和狀態的規格。|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|表示繫結至資料庫中的特定資料行的名稱。 支援有效位數和小數位數的指定。|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|表示繫結至資料庫中的特定資料行的名稱。 支援有效位數、 小數位數和資料行長度的規格。|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的有效位數、 小數位數、 資料行長度和資料行狀態的規格。|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的有效位數、 小數位數和資料行狀態的規格。|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料行狀態的規格。|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|表示繫結至資料庫中的特定資料行的名稱。 支援資料類型的規格。|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|表示繫結至資料庫中的特定資料行的名稱。 支援資料類型、 有效位數和小數位數的指定。|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型和大小的規格。|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型和資料行狀態的規格。|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|資料行對應項目結束標記。|  
  
### <a name="command-macros"></a>命令巨集  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|指定將用來建立資料列集，使用時的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 接受只比對指定的應用程式類型 （ANSI 或 Unicode） 字串類型。 建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`。|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|指定將用來建立資料列集，使用時的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 支援 ANSI 和 Unicode 應用程式。|  
  
### <a name="parameter-map-macros"></a>參數對應巨集  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|標記參數對應中的項目使用者記錄類別開頭。|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|參數對應項目結束標記。|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|指定`COLUMN_ENTRY`巨集，請遵循`SET_PARAM_TYPE`巨集做為輸入、 輸出或輸入/輸出。|  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)