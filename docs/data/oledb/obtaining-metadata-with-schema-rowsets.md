---
title: 使用結構描述資料列集取得中繼資料 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: da5a715be2ac6dc94ace25ee98781d2e9a4c5f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33114730"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>使用結構描述資料列集取得中繼資料
有時候您需要在未開啟資料列集的情況下取得提供者、資料列集、資料表、資料行或其他資料庫資訊的相關資訊。 有關資料庫結構的資料稱為中繼資料，並且可以由許多不同的方法擷取。 其中一個方法是使用結構描述資料列集。  
  
 OLE DB 樣板提供一組類別來擷取結構描述資訊;這些類別建立預先定義的結構描述資料列，而且會列於[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。  
  
> [!NOTE]
>  如果您是使用 OLAP，而且結構描述資料列集類別不支援您的一些資料列集 (例如，您具有變動的資料行數目)，則您應該考慮使用 `CManualAccessor` 或 `CDynamicAccessor`。 您可以捲動資料行，並使用 case 陳述式來處理每個資料行的可能資料型別。  
  
## <a name="catalogschema-model"></a>目錄/結構描述模型  
 ANSI SQL 會定義資料存放區的目錄/結構描述模型。OLE DB 會使用此模型。 在此模型中，目錄 (資料庫) 包含結構描述，而結構描述包含資料表。  
  
-   **目錄**目錄是資料庫的另一個名稱。 它是相關結構描述的集合。 若要列出屬於給定的資料來源的目錄 （資料庫），請使用[CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。 因為許多資料庫都只有一個目錄，所以中繼資料有時會簡稱為結構描述資訊。  
  
-   **結構描述**結構描述是資料庫物件所擁有或都由特定使用者的集合。 若要列出給定使用者所擁有的結構描述，請使用[CSchemata](../../data/oledb/cschemata-cschematainfo.md)。  
  
     在 Microsoft SQL Server 和 ODBC 2.x 詞彙中，結構描述是一位擁有者 （例如 dbo 是典型的結構描述名稱）。 此外，SQL Server 中的一組資料表，儲存中繼資料： 一個資料表包含所有資料表的清單，以及另一個資料表包含的所有資料行清單。 Microsoft Access 資料庫中沒有對等的結構描述。  
  
-   **資料表**資料表是以特定順序排列的資料行的集合。 若要列出的資料表定義中指定的目錄 （資料庫），這些資料表的相關資訊，請使用[CTables](../../data/oledb/ctables-ctableinfo.md))。  
  
## <a name="restrictions"></a>限制  
 當您查詢結構描述資訊時，您可以使用限制來指定您有興趣的資訊類型。 您可以將限制想成查詢中的篩選條件或限定詞。 例如，在查詢中：  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` 是限制。 這是非常簡單的範例，只有一個限制；結構描述資料列集類別支援數個限制。  
  
 [結構描述資料列集 typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)封裝所有 OLE DB 結構描述資料列，讓您可以存取的結構描述資料列集就像任何其他資料列具現化並將它開啟。 例如，typedef 類別[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)定義為：  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)類別提供限制支援。 您建立結構描述資料列集的執行個體之後，請呼叫[crestrictions:: Open](../../data/oledb/crestrictions-open.md)。 這個方法會根據您指定的限制傳回結果集。  
  
 若要指定限制，請參閱[附錄 b： 結構描述資料列集](http://go.microsoft.com/fwlink/p/?linkid=64681)並尋找您要使用的資料列集。 例如， **CColumns**對應至[COLUMNS 資料列集](http://go.microsoft.com/fwlink/p/?linkid=64682); 該主題列出 COLUMNS 資料列集的限制資料行： table_catalog 排列、 TABLE_SCHEMA、 TABLE_NAME、 COLUMN_NAME。 您必須依照該順序指定您的限制。  
  
 因此，比方說，如果您想要依資料表名稱限制，請注意 TABLE_NAME 是第三個限制資料行，然後呼叫**開啟**，做為第三個限制參數，指定所需的資料表名稱，如下列範例所示。  
  
#### <a name="to-use-schema-rowsets"></a>若要使用結構描述資料列集  
  
1.  您必須包含標頭檔 Atldbsch.h (當然，您也需要消費者支援的 Atldbcli.h)。  
  
2.  具現化消費者或文件標頭檔中的結構描述資料列集物件。 如果您想要資料表資訊，請將宣告**CTables**物件; 如果您想要資料行資訊，請將宣告**CColumns**物件。 此範例顯示如何擷取 authors 資料表中的資料行：  
  
    ```  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  若要擷取資訊，請存取結構描述資料列集物件的適當資料成員，例如 `ColumnSchemaRowset.m_szColumnName`。 這會對應至 COLUMN_NAME。 若要查看每個資料成員會對應到哪一個 OLE DB 資料行，請參閱[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。  
  
 如需結構描述資料列集的參考，typedef 類別提供於 OLE DB 樣板 (請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md))。  
  
 如需有關 OLE DB 結構描述資料列，包括限制資料行，請參閱[附錄 b： 結構描述資料列集](http://go.microsoft.com/fwlink/p/?linkid=64681)OLE DB 程式設計人員參考中。  
  
 如何使用結構描述資料列集類別的更複雜的範例，請參閱[CatDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)和[DBViewer](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)範例。  
  
 提供者支援的結構描述資料列集的相關資訊，請參閱[支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)