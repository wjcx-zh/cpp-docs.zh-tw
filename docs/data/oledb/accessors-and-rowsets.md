---
title: "存取子和資料列集 | Microsoft Docs"
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
  - "存取子 [C++]"
  - "存取子 [C++], 資料列集"
  - "陣列資料列集"
  - "大量資料列集"
  - "CAccessorBase 類別"
  - "CAccessorRowset 類別, 存取子類型"
  - "CArrayRowset 類別, 存取子"
  - "CBulkRowset 類別, 存取子"
  - "CRowset 類別, 存取子和資料列集"
  - "OLE DB 消費者樣板, 存取子"
  - "OLE DB 消費者樣板, 資料列集支援"
  - "資料列集 [C++], 存取"
  - "資料列集 [C++], 支援的類型"
  - "單一資料列集"
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 存取子和資料列集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 樣板會透過 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 類別使用存取子和資料列集，來設定和擷取資料。  這個類別可以處理不同型別的多重存取子。  
  
## 存取子型別  
 衍生自 [CAccessorBase](../../data/oledb/caccessorbase-class.md) 的所有存取子。  `CAccessorBase` 同時提供參數和資料行繫結。  
  
 下圖顯示存取子型別。  
  
 ![存取子類型](../../data/oledb/media/vcaccessortypes.png "vcAccessorTypes")  
存取子類別  
  
-   [CAccessor](../../data/oledb/caccessor-class.md)：當您在設計階段就知道資料庫來源的結構時，請使用這個存取子。  `CAccessor` 會靜態繫結包含緩衝區的資料庫記錄至資料來源。  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)：當您在設計階段不知道資料庫的結構時，請使用這個存取子。  `CDynamicAccessor` 呼叫 `IColumnsInfo::GetColumnInfo` 以取得資料庫資料行資訊。  它可以建立和管理存取子和緩衝區。  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)：請使用這個存取子來處理未知的命令類型。  `CDynamicParameterAccessor` 會在您準備命令時取得 `ICommandWithParameters` 介面的參數資訊 \(如果提供者可以支援 `ICommandWithParameters`\)。  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)、[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md) 和 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)：當您不知道資料庫的結構描述時，請使用這些類別。  `CDynamicStringAccessorA` 會將資料擷取為 ANSI 字串，`CDynamicStringAccessorW` 則會將資料擷取為 Unicode 字串。  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)：使用了這個類別，您就能在提供者可轉換型別的情況下，使用任何想要的資料型別。  它可以同時處理結果資料行和命令參數。  
  
 下表摘要了 OLE DB 樣板的存取子型別支援。  
  
|存取子型別|Dynamic|處理參數|緩衝區|多重存取子|  
|-----------|-------------|----------|---------|-----------|  
|`CAccessor`|沒有|有|使用者|有|  
|`CDynamicAccessor`|有|沒有|OLE DB 樣板|沒有|  
|`CDynamicParameterAccessor`|有|有|OLE DB 樣板|沒有|  
|`CDynamicStringAccessor[A,W]`|有|沒有|OLE DB 樣板|沒有|  
|`CManualAccessor`|有|有|使用者|有|  
  
## 資料列集型別  
 OLE DB 樣板支援三種資料列集 \(請參考上圖\)：單一資料列集 \(由 [CRowset](../../data/oledb/crowset-class.md) 實作\)、大量資料列集 \(由 [CBulkRowset](../../data/oledb/cbulkrowset-class.md) 實作\) 和陣列資料列集 \(由 [CArrayRowset](../../data/oledb/carrayrowset-class.md) 實作\)。  單一資料列集可以在呼叫 `MoveNext` 時擷取一個資料列控制代碼。  大量資料列集可以擷取多個資料列控制代碼。  陣列資料列集是可以使用陣列語法存取的資料列集。  
  
 下圖顯示資料列集型別。  
  
 ![RowsetType 圖形](../../data/oledb/media/vcrowsettypes.png "vcRowsetTypes")  
資料列集類別  
  
 [結構描述資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)不會存取資料存放區裡的資料，而是存取資料存放區的相關資訊，也就是中繼資料 \(Metadata\)。  結構描述 \(Schema\) 資料列集通常會使用於以下狀況：在編譯時期還不知道資料庫結構，但必須在執行階段取得該結構。  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)