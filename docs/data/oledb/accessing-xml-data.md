---
title: "存取 XML 資料 | Microsoft Docs"
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
  - "CStreamRowset 類別, 擷取 XML 資料"
  - "CXMLAccessor 類別, 擷取 XML 資料"
  - "資料 [C++], XML 資料存取"
  - "資料存取 [C++], XML 資料"
  - "資料列集 [C++], 擷取 XML 資料"
  - "XML [C++], 存取資料"
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 存取 XML 資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有兩種從資料來源擷取 XML 資料的不同方式：一種是使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)，另一種是使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  
  
|功能|CStreamRowset|CXMLAccessor|  
|--------|-------------------|------------------|  
|可傳送的資料量|一次擷取所有的資料行和資料列資料。|擷取所有的資料行資料，但是一次只能有一個資料列。  您必須使用 `MoveNext` 這類的方法來巡覽資料列。|  
|格式化字串|SQL Server 會格式化 XML 字串並將它傳送至消費者。|擷取具有原型格式 \(要求提供者以 Unicode 字串傳送\) 的資料列集資料，然後建置包含 XML 格式資料的字串。|  
|格式化的控制|您可以設定某些 SQL Server 2000 的特定屬性，以控制 XML 字串的格式化方式。|您無法控制產生的 XML 字串之格式。|  
  
 雖然 `CStreamRowset` 提供了一種整體來說是更有效率之擷取 XML 格式資料的方式，但是只有 SQL Server 2000 才支援這種方法。  
  
## 使用 CStreamRowset 擷取 XML 資料  
 您可以在 `CCommand` 或 `CTable` 宣告中將 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 指定成資料列集類型。  您可以將它用在您自己的存取子或不用任何存取子，例如：  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 \-或\-  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 通常當您呼叫 `CCommand::Open` 時 \(例如，指定 `CRowset` 為 `TRowset` 類別\)，它會取得 `IRowset`指標。  `ICommand::Execute` 會傳回 `IRowset`指標，此指標儲存於 `CRowset` 物件的 `m_spRowset` 成員中。  `MoveFirst`、`MoveNext` 和 `GetData` 這類方法會使用此指標擷取資料。  
  
 相反地，`ICommand::Execute` 會在您呼叫 `CCommand::Open` 時 \(卻將 `CStreamRowset` 指定為 `TRowset` 類別\)，傳回儲存於 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 的 `m_spStream` 資料成員中的 `ISequentialStream` 指標。  然後您可以使用 `Read` 方法以擷取 XML 格式的資料 \(Unicode 字串\)。  例如：  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 會執行 XML 格式化，並將資料列集的所有資料行和資料列以 XML 字串傳回。  
  
 如需使用 `Read` 方法的範例，請參閱[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)內的＜加入 XML 支援至消費者＞。  
  
> [!NOTE]
>  使用 `CStreamRowset` 的 XML 支援僅適用於 SQL Server 2000，而且要求您擁有 SQL Server 2000 的 OLE DB 提供者 \(和 MDAC 一起安裝\)。  
  
## 使用 CXMLAccessor 擷取 XML 資料  
 當您不了解資料存放區的結構描述時，[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) 能讓您將資料來源的資料存取為字串。  除了能把從資料存放區存取的所有資料轉換為 XML 格式 \(加上標記\) 資料以外，`CXMLAccessor` 的其他作用就如同 `CDynamicStringAccessorW`。  XML 標記名稱盡量符合資料存放區的資料行名稱。  
  
 使用其他存取子類別的存取方式以使用 `CXMLAccessor`，將其當成樣板參數傳遞給 `CCommand` 或 `CTable`：  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 使用 [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)，從資料表一次一個資料列地擷取資料，並使用 `MoveNext` 這類方法來巡覽資料列，例如：  
  
```  
// Open data source, session, and rowset  
hr = rs.MoveFirst();  
while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
{  
    CStringW strRowData;  
    myCmd.GetXMLRowData(strRowData);  
  
    printf_s( "%S\n", strRowData );  
  
    hr = rs.MoveNext();  
}  
```  
  
 您可以使用 [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)，以 XML 格式字串資料方式擷取資料行 \(資料型別\) 資訊。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)