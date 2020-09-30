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
ms.openlocfilehash: 437f1d103420ec5727294894c02587c68cffbdda
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509124"
---
# <a name="accessing-xml-data"></a>存取 XML 資料

從資料來源抓取 XML 資料有兩種不同的方法：一個使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) ，另一個則使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。

|功能|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|傳輸的資料量|一次抓取所有資料行和資料列的資料。|從所有資料行，但一次只抓取一個資料列。 您必須使用像這樣的方法來流覽資料列 `MoveNext` 。|
|格式化字串|SQL Server 會格式化 XML 字串，並將它傳送給取用者。|以原生格式抓取資料列集資料 (要求提供者將其傳送為 Unicode 字串) 然後建立以 XML 格式保存資料的字串。|
|控制格式化|您可以藉由設定某些 SQL Server 2000 特定的屬性，對 XML 字串的格式設定有某種程度的控制。|您無法控制產生的 XML 字串格式。|

雖然 `CStreamRowset` 提供更有效率的方式來抓取 XML 格式的資料，但只有 SQL Server 2000 支援。

## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 抓取 XML 資料

您可以在或宣告中將 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 指定為數據列集類型 `CCommand` `CTable` 。 您可以使用它來搭配您自己的存取子或無存取子，例如：

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-或-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

一般來說，當您呼叫 `CCommand::Open` (指定（例如 `CRowset` `TRowset`) 類別）時，它會取得 `IRowset` 指標。 `ICommand::Execute` 傳回 `IRowset` 指標，該指標儲存在物件的 `m_spRowset` 成員中 `CRowset` 。 方法（例如 `MoveFirst` 、 `MoveNext` 和） `GetData` 會使用該指標來取得資料。

相反地，當您呼叫 `CCommand::Open` (但指定 `CStreamRowset` 為 `TRowset`) 類別時， `ICommand::Execute` 會傳回 `ISequentialStream` 指標，該指標儲存在 `m_spStream` [CStreamRowset](../../data/oledb/cstreamrowset-class.md)的資料成員中。 然後，您可以使用 `Read` 方法，以 XML 格式來取得 (的 Unicode 字串) 資料。 例如：

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 會進行 XML 格式設定，並傳回資料列集的所有資料行和所有資料列做為一個 XML 字串。

如需使用方法的範例 `Read` ，請參閱在[執行簡單取用者](../../data/oledb/implementing-a-simple-consumer.md)時，**將 XML 支援加入至取用者**。

> [!NOTE]
> 使用 `CStreamRowset` 僅適用于 SQL Server 2000 的 XML 支援，而且需要您具備使用 MDAC) 安裝 SQL Server 2000 (的 OLE DB 提供者。

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 抓取 XML 資料

當您不知道資料存放區的架構時， [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)可讓您以字串資料的形式存取資料來源中的資料。 `CXMLAccessor` 運作方式類似 `CDynamicStringAccessorW` ，但前者會將從資料存放區存取的所有資料轉換為 XML 格式的 (標記為) 資料。 XML 標記名稱會與資料存放區的資料行名稱盡可能相符。

`CXMLAccessor`如同任何其他存取子類別一樣，以範本參數形式傳遞給 `CCommand` 或 `CTable` ：

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

使用 [GetXMLRowData](./cxmlaccessor-class.md#getxmlrowdata) 一次從一個資料列取出資料表中的資料，並使用像是的方法來流覽資料列，例如 `MoveNext` ：

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

您可以使用 [GetXMLColumnData](./cxmlaccessor-class.md#getxmlcolumndata) ，將資料行 (資料類型) 資訊以 XML 格式的字串資料的形式取得。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
