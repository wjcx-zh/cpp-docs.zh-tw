---
title: 使用結構描述資料列集取得中繼資料
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 37418cc91913ed840d1601aab9005b476bf29ee0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508990"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>使用結構描述資料列集取得中繼資料

有時候您需要在未開啟資料列集的情況下取得提供者、資料列集、資料表、資料行或其他資料庫資訊的相關資訊。 有關資料庫結構的資料稱為中繼資料，並且可以由許多不同的方法擷取。 其中一個方法是使用結構描述資料列集。

OLE DB 範本會提供一組用來取出架構資訊的類別;這些類別會建立預先定義的架構資料列集，且會列在架構資料列 [集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)中。

> [!NOTE]
> 如果您是使用 OLAP，而且結構描述資料列集類別不支援您的一些資料列集 (例如，您具有變動的資料行數目)，則您應該考慮使用 `CManualAccessor` 或 `CDynamicAccessor`。 您可以捲動資料行，並使用 case 陳述式來處理每個資料行的可能資料型別。

## <a name="catalogschema-model"></a>目錄/結構描述模型

ANSI SQL 會定義資料存放區的目錄/結構描述模型。OLE DB 會使用此模型。 在此模型中， (資料庫的目錄) 具有資料表的架構和架構。

- **目錄** 目錄是資料庫的另一個名稱。 它是一組相關的架構。 若要列出屬於給定資料來源 (資料庫) 的目錄，請使用 [CCatalog](./schema-rowset-classes-and-typedef-classes.md#catalog)。 因為許多資料庫只有一個目錄，所以中繼資料有時稱為架構資訊。

- **架構** 架構是由特定使用者所擁有或已建立的資料庫物件集合。 若要列出指定使用者所擁有的架構，請使用 [CSchemata](./schema-rowset-classes-and-typedef-classes.md#schemata)。

   在 Microsoft SQL Server 和 ODBC 2.x 詞彙中，結構描述是一位擁有者 (例如 dbo 是典型的結構描述名稱)。 此外，SQL Server 會以一組資料表儲存中繼資料：一個資料表包含所有資料表的清單，而另一個資料表包含所有資料行的清單。 Microsoft Access 資料庫中的架構沒有任何等同專案。

- **資料表** 資料表是以特定順序排列的資料行集合。 若要列出指定目錄中定義的資料表 (資料庫) 以及這些資料表的相關資訊，請使用 [CTables](./schema-rowset-classes-and-typedef-classes.md#table)) 。

## <a name="restrictions"></a>限制

當您查詢架構資訊時，您可以使用限制來指定您感興趣的資訊類型。 您可以將限制想成查詢中的篩選條件或限定詞。 例如，在查詢中：

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` 是限制。 這是只有一項限制的簡單範例;架構資料列集類別支援數項限制。

架構資料列 [集 typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) 會封裝所有 OLE DB 架構資料列集，讓您可以像任何其他資料列集一樣存取架構資料列集，方法是將它具現化並加以開啟。 例如，typedef 類別 [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns) 定義為：

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md)類別會提供限制支援。 在您建立架構資料列集的實例之後，請呼叫 [CRestrictions：： Open](./crestrictions-class.md#open)。 這個方法會根據您指定的限制傳回結果集。

若要指定限制，請參閱 [附錄 B：架構](/previous-versions/windows/desktop/ms712921(v=vs.85)) 資料列集，並查閱您所使用的資料列集。 例如， `CColumns` 對應至資料 [行資料列集](/previous-versions/windows/desktop/ms723052(v=vs.85)); 該主題會列出資料行資料列集中的限制資料行： TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME COLUMN_NAME。 您必須依照該順序指定您的限制。

因此，舉例來說，如果您想要依資料表名稱限制，TABLE_NAME 是第三個限制資料行，然後呼叫 `Open` ，將需要的資料表名稱指定為第三個限制參數，如下列範例所示。

### <a name="to-use-schema-rowsets"></a>若要使用結構描述資料列集

1. `Atldbsch.h`您也可以將標頭檔 (在取用 `Atldbcli.h` 者支援) 。

1. 具現化消費者或文件標頭檔中的結構描述資料列集物件。 如果您想要資料表資訊，請宣告 `CTables` 物件; 如果您想要資料行資訊，請宣告 `CColumns` 物件。 此範例顯示如何擷取 authors 資料表中的資料行：

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

1. 若要擷取資訊，請存取結構描述資料列集物件的適當資料成員，例如 `ColumnSchemaRowset.m_szColumnName`。 此資料成員會對應至 COLUMN_NAME。 若要查看每個資料成員對應的 OLE DB 資料行，請參閱 [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns)。

如需架構資料列集的參考，OLE DB 範本中提供的 typedef 類別 (參閱架構資料列 [集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)) 。

如需 OLE DB 架構資料列集的詳細資訊，包括限制資料行，請參閱 OLE DB 程式設計**人員參考**中的[附錄 B：架構](/previous-versions/windows/desktop/ms712921(v=vs.85))資料列集。

如需如何使用架構資料列集類別的更複雜範例，請參閱 [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 和 [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 範例。

如需架構資料列集的提供者支援詳細資訊，請參閱 [支援架構](../../data/oledb/supporting-schema-rowsets.md)資料列集。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
