---
title: "命令和資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorRowset 類別, 命令和資料表類別"
  - "CCommand 類別, OLE DB 消費者樣板"
  - "命令 [C++], OLE DB 消費者樣板"
  - "CTable 類別"
  - "OLE DB 消費者樣板, 命令支援"
  - "OLE DB 消費者樣板, 資料表支援"
  - "資料列集, 存取"
  - "資料表 [C++], OLE DB 消費者樣板"
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 命令和資料表
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命令和資料表可以讓您存取資料列集，也就是開啟資料列集、執行命令，以及繫結資料行。  [CCommand](../../data/oledb/ccommand-class.md) 和 [CTable](../../data/oledb/ctable-class.md) 類別會分別產生命令和資料表物件。  這些類別會依照下圖所示方式，從 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 衍生出來。  
  
 ![CCommand 和 CTable](../../data/oledb/media/vccommandstables.png "vcCommandsTables")  
命令和資料表類別  
  
 在上述資料表中，`TAccessor` 可以是列於[存取子型別](../../data/oledb/accessors-and-rowsets.md)的任何一種存取子型別。  *TRowset* 可以是[資料列集類型](../../data/oledb/accessors-and-rowsets.md)中所列出的任何一種資料列集類型。  *TMultiple* 可以指定結果類型 \(單一或多重結果集\)。  
  
 [ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)可以讓您指定您需要的是命令或資料表物件。  
  
-   您可以為不具命令的資料來源使用 `CTable` 類別。  通常您會將這種類別使用於指定沒有參數和不需要多重結果的簡單資料列集。  這個簡單類別會使用指定的資料表名稱，開啟資料來源上的資料表。  
  
-   針對支援命令的資料來源，您可以改用 `CCommand` 類別。  若要執行命令，請在這個類別上呼叫 [Open](../../data/oledb/ccommand-open.md)。  另一種方法是，呼叫 `Prepare` 以準備希望多次執行的命令。  
  
     **CCommand**  有三個樣板引數 \(Template Argument\)：存取子型別、資料列集型別和結果型別 \(預設值為 `CNoMultipleResults` 或 `CMultipleResults`\)。  如果您指定了 `CMultipleResults`，`CCommand` 類別便可以支援 **IMultipleResults** 介面及處理多重資料列集。  [DBVIEWER](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832) 範例顯示了多重資料列集的處理方式。  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)