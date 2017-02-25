---
title: "使用結構描述資料列集取得中繼資料 | Microsoft Docs"
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
  - "中繼資料, 取得 (OLE DB 樣板)"
  - "OLE DB 消費者樣板, 取得提供者中繼資料"
  - "結構描述資料列集, 取得 OLE DB 提供者中繼資料"
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用結構描述資料列集取得中繼資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有時候您需要在未開啟資料列集的情況下取得提供者、資料列集、資料表、資料行或其他資料庫資訊的相關資訊。  有關資料庫結構的資料稱為中繼資料，並且可以由許多不同的方法擷取。  其中一個方法是使用結構描述資料列集。  
  
 OLE DB 樣板提供一組類別來擷取結構描述資訊；這些類別會建立預先定義的結構描述資料列，並且列示在 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)中。  
  
> [!NOTE]
>  如果您是使用 OLAP，而且結構描述資料列集類別不支援您的一些資料列集 \(例如，您具有變動的資料行數目\)，則您應該考慮使用 `CManualAccessor` 或 `CDynamicAccessor`。  您可以捲動資料行，並使用 case 陳述式來處理每個資料行的可能資料型別。  
  
## 目錄\/結構描述模型  
 ANSI SQL 會定義資料存放區的目錄\/結構描述模型。OLE DB 會使用此模型。  在此模型中，目錄 \(資料庫\) 包含結構描述，而結構描述包含資料表。  
  
-   **目錄** 目錄是資料庫的另一個名稱。  它是相關結構描述的集合。  若要列出屬於給定資料來源的目錄 \(資料庫\)，請使用 [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。  因為許多資料庫都只有一個目錄，所以中繼資料有時會簡稱為結構描述資訊。  
  
-   **結構描述** 結構描述是特定使用者所擁有或建立的資料庫物件集合。  若要列出給定使用者所擁有的結構描述，請使用 [CSchemata](../../data/oledb/cschemata-cschematainfo.md)。  
  
     在 Microsoft SQL Server 和 ODBC 2.x 詞彙中，結構描述是一位擁有者 \(例如 dbo 是典型的結構描述名稱\)。  此外，SQL Server 會以一組資料表儲存中繼資料：一個資料表包含所有資料表的清單，而另一個資料表包含所有資料行的清單。  Microsoft Access 資料庫中沒有對等的結構描述。  
  
-   **資料表** 資料表是以特定順序排列的資料行集合。  若要列出給定目錄 \(資料庫\) 中定義的資料表，以及那些資料表的相關資訊，請使用 [CTables](../../data/oledb/ctables-ctableinfo.md)。  
  
## 限制  
 當您查詢結構描述資訊時，您可以使用限制來指定您有興趣的資訊類型。  您可以將限制想成查詢中的篩選條件或限定詞。  例如，在查詢中：  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` 是限制。  這是非常簡單的範例，只有一個限制；結構描述資料列集類別支援數個限制。  
  
 [結構描述資料列集 typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)會封裝所有 OLE DB 結構描述資料列，讓您得以具現化結構描述資料列集並將它開啟來進行存取，就像任何其他資料列集一樣。  例如，typedef 類別 [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) 定義為：  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md) 類別提供限制支援。  建立結構描述資料列集的執行個體之後，請呼叫 [CRestrictions::Open](../../data/oledb/crestrictions-open.md)。  這個方法會根據您指定的限制傳回結果集。  
  
 若要指定限制，請參閱[附錄 B：結構描述資料列集](http://go.microsoft.com/fwlink/?LinkId=64681)，並尋找您要使用的資料列集。  例如，**CColumns** 對應至 [COLUMNS 資料列集](http://go.microsoft.com/fwlink/?LinkId=64682)；該主題列出 COLUMNS 資料列集的限制資料行：TABLE\_CATALOG、TABLE\_SCHEMA、TABLE\_NAME、COLUMN\_NAME。  您必須依照該順序指定您的限制。  
  
 因此，比方說，如果您想要依資料表名稱限制，請注意 TABLE\_NAME 是第三個限制資料行，然後呼叫 \[**開啟**\]，做為第三個限制參數，指定所需的資料表名稱，如下列範例所示。  
  
#### 若要使用結構描述資料列集  
  
1.  您必須包含標頭檔 Atldbsch.h \(當然，您也需要消費者支援的 Atldbcli.h\)。  
  
2.  具現化消費者或文件標頭檔中的結構描述資料列集物件。  如果您想要資料表資訊，請宣告 **CTables** 物件；如果您想要資料行資訊，請宣告 **CColumns** 物件。  此範例顯示如何擷取 authors 資料表中的資料行：  
  
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
  
3.  若要擷取資訊，請存取結構描述資料列集物件的適當資料成員，例如 `ColumnSchemaRowset.m_szColumnName`。  這會對應至 COLUMN\_NAME。  若要查看每個資料成員對應到哪一個 OLE DB 資料行，請參閱 [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。  
  
 如需結構描述資料列的參考，typedef 類別提供於 OLE DB 樣板 \(請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)\)。  
  
 如需 OLE DB 結構描述資料列集的詳細資訊，包括限制資料行，請參閱《OLE DB 程式設計人員參考》中的[附錄 B：結構描述資料列集](http://go.microsoft.com/fwlink/?LinkId=64681)。  
  
 如需更多如何使用結構描述資料列集類別的複雜範例，請參閱 [CatDB](http://msdn.microsoft.com/zh-tw/003d516b-2bf6-444e-8be5-4ebaa0b66046) 和 [DBViewer](http://msdn.microsoft.com/zh-tw/07620f99-c347-4d09-9ebc-2459e8049832) 範例。  
  
 如需結構描述資料列之提供者支援的相關資訊，請參閱[支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)