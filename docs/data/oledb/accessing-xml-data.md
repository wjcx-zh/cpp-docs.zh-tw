---
title: 存取 XML 資料
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: be4225003211449a98d3fbe5fd686b9b8058a651
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212273"
---
# <a name="accessing-xml-data"></a>存取 XML 資料

有兩種不同的方法可從資料來源抓取 XML 資料：一個使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md) ，另一個則使用[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。

|功能|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|傳輸的資料量|一次從所有資料行和資料列抓取資料。|從所有資料行（但一次只一個資料列）抓取資料。 您必須使用 `MoveNext`之類的方法來流覽資料列。|
|格式化字串|SQL Server 會格式化 XML 字串，並將它傳送給取用者。|以原生格式（要求提供者將其傳送為 Unicode 字串）來抓取資料列集，然後建立以 XML 格式保存資料的字串。|
|控制格式化|藉由設定一些 SQL Server 2000 特有的屬性，您可以控制 XML 字串的格式化方式。|您無法控制所產生之 XML 字串的格式。|

雖然 `CStreamRowset` 提供更有效率的方式來以 XML 格式抓取資料，但只有 SQL Server 2000 才支援。

## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 來抓取 XML 資料

您可以在 `CCommand` 或 `CTable` 宣告中，將[CStreamRowset](../../data/oledb/cstreamrowset-class.md)指定為數據列集類型。 您可以將它與您自己的存取子或沒有存取子搭配使用，例如：

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-或-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

通常當您呼叫 `CCommand::Open` （例如，將 `CRowset` 指定為 `TRowset` 類別）時，它會取得 `IRowset` 指標。 `ICommand::Execute` 會傳回 `IRowset` 指標，其儲存在 `CRowset` 物件的 `m_spRowset` 成員中。 `MoveFirst`、`MoveNext`和 `GetData` 等方法會使用該指標來抓取資料。

相反地，當您呼叫 `CCommand::Open` （但指定 `CStreamRowset` 做為 `TRowset` 類別）時，`ICommand::Execute` 會傳回 `ISequentialStream` 指標，這會儲存在[CStreamRowset](../../data/oledb/cstreamrowset-class.md)的 `m_spStream` 資料成員中。 然後，您可以使用 `Read` 方法，以 XML 格式抓取（Unicode 字串）資料。 例如：

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 會進行 XML 格式設定，並傳回資料列集的所有資料行和資料列，做為一個 XML 字串。

如需使用 `Read` 方法的範例，請參閱在[執行簡單取用者](../../data/oledb/implementing-a-simple-consumer.md)中**將 XML 支援新增至取用者**。

> [!NOTE]
> 使用 `CStreamRowset` 的 XML 支援僅適用于 SQL Server 2000，而且您必須擁有 SQL Server 2000 的 OLE DB 提供者（使用 MDAC 安裝）。

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 來抓取 XML 資料

當您不知道資料存放區的架構時， [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)可讓您以字串資料的形式，存取資料來源中的資料。 `CXMLAccessor` 的運作方式類似 `CDynamicStringAccessorW`，不同之處在于前者會將從資料存放區存取的所有資料轉換為 XML 格式（標記）的資料。 XML 標記名稱會盡可能符合資料存放區的資料行名稱。

如同任何其他存取子類別，使用 `CXMLAccessor`，將它當做樣板參數傳遞給 `CCommand` 或 `CTable`：

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

您可以使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) ，一次從資料表中取出資料，並使用像是 `MoveNext`的方法來流覽資料列，例如：

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

您可以使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) ，以 XML 格式的字串資料來抓取資料行（資料類型）資訊。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
