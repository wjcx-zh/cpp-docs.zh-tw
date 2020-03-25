---
title: 使用結構描述資料列集取得中繼資料
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: e04b9a335c60cefdc28be2347ef1f0762c424d8e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210128"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>使用結構描述資料列集取得中繼資料

有時候您需要在未開啟資料列集的情況下取得提供者、資料列集、資料表、資料行或其他資料庫資訊的相關資訊。 有關資料庫結構的資料稱為中繼資料，並且可以由許多不同的方法擷取。 其中一個方法是使用結構描述資料列集。

OLE DB 範本會提供一組類別來取得架構資訊;這些類別會建立預先定義的架構資料列集，並列出在架構資料列[集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)中。

> [!NOTE]
> 如果您是使用 OLAP，而且結構描述資料列集類別不支援您的一些資料列集 (例如，您具有變動的資料行數目)，則您應該考慮使用 `CManualAccessor` 或 `CDynamicAccessor`。 您可以捲動資料行，並使用 case 陳述式來處理每個資料行的可能資料型別。

## <a name="catalogschema-model"></a>目錄/結構描述模型

ANSI SQL 會定義資料存放區的目錄/結構描述模型。OLE DB 會使用此模型。 在此模型中，目錄（資料庫）的架構和架構都有資料表。

- **目錄**目錄是資料庫的另一個名稱。 這是一組相關的架構。 若要列出屬於給定資料來源的目錄（資料庫），請使用[CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。 因為許多資料庫只有一個目錄，中繼資料有時也稱為架構資訊。

- **架構**「架構」（schema）是由特定使用者所擁有或已建立之資料庫物件的集合。 若要列出指定使用者所擁有的架構，請使用[CSchemata](../../data/oledb/cschemata-cschematainfo.md)。

   在 Microsoft SQL Server 和 ODBC 2.x 詞彙中，架構是擁有者（例如，dbo 是一般的架構名稱）。 此外，SQL Server 會將中繼資料儲存在一組資料表中：一個資料表包含所有資料表的清單，而另一個資料表則包含所有欄位的清單。 在 Microsoft Access 資料庫中，沒有任何對等的架構。

- **資料表**資料表是以特定順序排列的資料行集合。 若要列出指定目錄（資料庫）中所定義的資料表，以及這些資料表的相關資訊，請使用[CTables](../../data/oledb/ctables-ctableinfo.md)）。

## <a name="restrictions"></a>限制

當您查詢架構資訊時，您可以使用限制來指定您感興趣的資訊類型。 您可以將限制想成查詢中的篩選條件或限定詞。 例如，在查詢中：

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` 是限制。 這是一個簡單的範例，只有一個限制;架構資料列集類別支援數個限制。

架構資料列[集 typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)會封裝所有 OLE DB 架構資料列集，讓您可以藉由具現化和開啟架構資料列集，就像任何其他資料列集一樣地存取它。 例如，typedef 類別[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)定義為：

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md)類別會提供限制支援。 建立架構資料列集的實例之後，請呼叫[CRestrictions：： Open](../../data/oledb/crestrictions-open.md)。 這個方法會根據您指定的限制傳回結果集。

若要指定限制，請參閱[附錄 B：架構](/previous-versions/windows/desktop/ms712921(v=vs.85))資料列集，並查閱您所使用的資料列集。 例如，`CColumns` 對應至資料[行資料列集](/previous-versions/windows/desktop/ms723052(v=vs.85));該主題會列出 COLUMNS 資料列集中的限制資料行： TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME、COLUMN_NAME。 您必須依照該順序指定您的限制。

因此，例如，如果您想要依資料表名稱來限制，TABLE_NAME 是第三個限制資料行，然後呼叫 `Open`，將所需的資料表名稱指定為第三個限制參數，如下列範例所示。

### <a name="to-use-schema-rowsets"></a>若要使用結構描述資料列集

1. 包括標頭檔 `Atldbsch.h` （也需要取用者支援 `Atldbcli.h`）。

1. 具現化消費者或文件標頭檔中的結構描述資料列集物件。 如果您想要資料表資訊，請宣告 `CTables` 物件;如果您想要資料行資訊，請宣告 `CColumns` 物件。 此範例顯示如何擷取 authors 資料表中的資料行：

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. 若要擷取資訊，請存取結構描述資料列集物件的適當資料成員，例如 `ColumnSchemaRowset.m_szColumnName`。 這個資料成員會對應到 COLUMN_NAME。 若要查看每個資料成員對應的 OLE DB 資料行，請參閱[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。

如需架構資料列集的參考，OLE DB 範本中提供的 typedef 類別（請參閱架構資料列[集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)）。

如需 OLE DB 架構資料列集的詳細資訊，包括限制資料行，請參閱[附錄 B：](/previous-versions/windows/desktop/ms712921(v=vs.85)) OLE DB 程式設計**人員參考**中的架構資料列集。

如需如何使用架構資料列集類別的更複雜範例，請參閱[CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)和[DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)範例。

如需架構資料列集之提供者支援的詳細資訊，請參閱[支援架構](../../data/oledb/supporting-schema-rowsets.md)資料列集。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
