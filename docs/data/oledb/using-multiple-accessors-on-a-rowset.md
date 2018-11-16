---
title: 在資料列集上使用多重存取子
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: ac2b7e323fff5d3baa80b509586178a48dbe1f8d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693616"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>在資料列集上使用多重存取子

有三個基本的情況下，您需要使用多重存取子：

- **多個讀取/寫入資料列集。** 在此案例中，您會有具有主索引鍵的資料表。 您想要能夠讀取的資料列，包括主索引鍵中的所有資料行。 您也要能夠將資料寫入至主索引鍵以外的所有資料行，（因為您無法寫入主要索引鍵資料行）。 在此情況下，您會設定兩個存取子：

  - 包含所有資料行存取子 0。

  - 存取子 1 包含的主索引鍵以外的所有資料行。

- **效能。** 在此案例中，一或多個資料行有大量的資料，例如圖形、 音訊或視訊檔。 每次您移至一個資料列，您可能不想要擷取資料行，將大型資料檔案因為這麼做會降低您的應用程式效能。

  您可以設定個別存取子中的第一個存取子包含大型的資料以外的所有資料行和它的資料會從擷取這些資料行，而第一個存取子是自動存取子。 第二個存取子擷取保留大型的資料，資料行，但它不會自動擷取資料從這個資料行。 您可以有其他更新，或依需求擷取大型資料的方法。

  - 存取子 0 是自動的存取子;它會擷取大型資料以外的所有資料行。

  - 存取子 1 不是自動的存取子;它會擷取大型資料的資料行。

  若要指定存取子是否自動存取子中使用的自動引數。

- **多個的 ISequentialStream 資料行。** 在此案例中，您已經一個以上的資料行保存`ISequentialStream`資料。 不過，每個存取子僅限一份`ISequentialStream`資料流。 若要解決此問題，請設定數個存取子，各自擁有一個`ISequentialStream`指標。

您通常會建立使用存取子[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。 您也可以使用[db_accessor](../../windows/db-accessor.md)屬性。 (存取子會進一步說明，在[使用者記錄](../../data/oledb/user-records.md)。)巨集或屬性指定是否自動或非自動存取子的存取子：

- 在自動存取子，移動方法這類`MoveFirst`， `MoveLast`， `MoveNext`，和`MovePrev`所有指定自動的資料行擷取資料。 存取子 0 應該是自動的存取子。

- 在非自動存取子擷取不會發生直到您明確地呼叫方法這類`Update`， `Insert`， `Fetch`，或`Delete`。 在上面所述的案例中，您可能不想要擷取在每次移動的所有資料行。 您可以將一或多個資料行放在不同的存取子，並將該有非自動存取子，如下所示。

下列範例會使用多個存取子來讀取和寫入作業的資料庫資料表的 SQL Server pubs 使用多重存取子。 這個範例是最常用的多個存取子;請參閱上述 「 多個讀取/寫入資料列集 」 案例。

使用者記錄類別如下所示。 它會設定兩個存取子： 包含僅主要索引鍵資料行 (ID) 的存取子 0 和 1 的存取子包含其他資料行。

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

主要的程式碼如下所示。 呼叫`MoveNext`自動將資料擷取使用存取子 0 的主索引鍵資料行識別碼。 請注意如何`Insert`附近會使用存取子 1，來避免寫入主要索引鍵資料行的方法。

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[使用者資料錄](../../data/oledb/user-records.md)
