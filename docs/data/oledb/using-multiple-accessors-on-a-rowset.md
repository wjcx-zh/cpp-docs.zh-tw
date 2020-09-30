---
title: 在資料列集上使用多重存取子
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 48772539b4dda9262a244506a36932d1e752949e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509398"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>在資料列集上使用多重存取子

有三種基本案例，您需要使用多個存取子：

- **多個讀取/寫入資料列集。** 在此案例中，您有一個具有主鍵的資料表。 您想要能夠讀取資料列中的所有資料行，包括主要索引鍵。 您也想要能夠將資料寫入到主鍵 (以外的所有資料行，因為您無法寫入主鍵資料行) 。 在此情況下，您會設定兩個存取子：

  - 存取子0包含所有資料行。

  - 存取子1包含主鍵以外的所有資料行。

- **效能。** 在此案例中，有一或多個資料行有大量的資料，例如，圖形、音效或影片檔案。 每次移至某個資料列時，您可能不會想要使用大型資料檔案抓取資料行，因為這樣做會讓您的應用程式效能變慢。

  您可以設定個別存取子，其中第一個存取子包含具有大型資料的所有資料行，而且它會自動從這些資料行中取出資料。第一個存取子是自動存取子。 第二個存取子只會取出保存大型資料的資料行，但不會自動從這個資料行中取出資料。 您可以讓其他方法視需要更新或提取大型資料。

  - 存取子0是自動存取子;它會抓取包含大型資料的所有資料行。

  - 存取子1不是自動存取子;它會抓取具有大型資料的資料行。

  您可以使用 auto 引數來指定存取子是否為自動存取子。

- **多個 ISequentialStream 資料行。** 在此案例中，您有多個資料行保留 `ISequentialStream` 資料。 不過，每個存取子只能有一個 `ISequentialStream` 資料流程。 若要解決這個問題，請設定數個存取子，每個存取子都有一個 `ISequentialStream` 指標。

您通常會使用 [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) 和 [END_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) 宏來建立存取子。 您也可以使用 [db_accessor](../../windows/attributes/db-accessor.md) 屬性。  (存取子會在 [使用者記錄](../../data/oledb/user-records.md)中進一步描述。 ) 宏或屬性指定存取子是否為自動或非自動存取子：

- 在自動存取子中，會自動移動方法（例如 `MoveFirst` 、、和），以 `MoveLast` `MoveNext` `MovePrev` 自動取得所有指定資料行的資料。 存取子0應該是自動存取子。

- 在非自動存取子中，除非您明確呼叫方法（例如 `Update` 、、或），否則不會進行抓取 `Insert` `Fetch` `Delete` 。 在上述案例中，您可能不想要在每次移動時取出所有資料行。 您可以將一或多個資料行放在不同的存取子，並使其成為非自動存取子，如下所示。

下列範例會使用多個存取子，以使用多個存取子來讀取和寫入 SQL Server pubs 資料庫的工作資料表。 此範例是多個存取子的最常見用法;請參閱上面的「多個讀取/寫入資料列集」案例。

使用者記錄類別如下所示。 它會設定兩個存取子：存取子0只包含主鍵資料行 (識別碼) ，而存取子1則包含其他資料行。

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

主要程式碼如下所示。 呼叫 `MoveNext` 會自動使用存取子0從主鍵資料行識別碼中取出資料。 請注意， `Insert` 接近 end 的方法如何使用存取子1來避免寫入主鍵資料行。

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
[使用者記錄](../../data/oledb/user-records.md)
