---
title: "資料列集上使用多重存取子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 06a9e668ecf2a16a933a9accd727284fa0f4bab6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="using-multiple-accessors-on-a-rowset"></a>在資料列集上使用多重存取子
有三個您要使用多重存取子的基本案例：  
  
-   **多個讀取/寫入資料列集。** 在此案例中，您必須具有主索引鍵的資料表。 要讀取的資料列，包括主索引鍵中的所有資料行。 您也想要能夠寫入以外的主索引鍵的所有資料行的資料 （因為您無法寫入主要索引鍵資料行）。 在此情況下，您設定兩個存取子：  
  
    -   包含所有資料行存取子 0。  
  
    -   存取子 1 包含所有其他的主索引鍵資料行。  
  
-   **效能。** 在此案例中，一或多個資料行包含大量資料，例如圖形、 語音或視訊檔。 每次您移至資料列，可能不想擷取資料行與大型資料檔案，因為這樣做會降低應用程式的效能。  
  
     您可以設定個別存取子中的第一個存取子包含大型的資料以外的所有資料行和資料從擷取這些資料行，而這是自動存取子。 第二個存取子擷取包含大型的資料的資料行，但它不會擷取資料從這個資料行自動。 您可以有其他方法更新，或視擷取大型資料。  
  
    -   存取子 0 是自動存取子。它會擷取大型資料以外的所有資料行。  
  
    -   存取子 1 不是自動存取子。它會擷取大型資料的資料行。  
  
     您可以使用的自動引數來指定存取子是否自動存取子。  
  
-   **多個 ISequentialStream 資料行。** 在此案例中，您有多個資料行包含`ISequentialStream`資料。 不過，每個存取子僅限於一個`ISequentialStream`資料流。 若要解決這個問題，設定數個存取子中，每一個都會包含一個`ISequentialStream`指標。  
  
 您通常會建立存取子使用[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。 您也可以使用[db_accessor](../../windows/db-accessor.md)屬性。 (存取子是更進一步的說明[使用者資料錄](../../data/oledb/user-records.md)。)巨集或屬性指定是否自動或非自動存取子的存取子：  
  
-   在自動存取子中，移動方法例如**MoveFirst**， `MoveLast`， `MoveNext`，和`MovePrev`所有自動指定資料行擷取資料。 存取子 0 應該自動存取子。  
  
-   非自動存取子中擷取不會明確地呼叫方法例如**更新**，**插入**，**提取**，或**刪除**. 在上述情況下，您可能不想擷取每次移動的所有資料行。 您可以置於個別的存取子中的一或多個資料行，並使該非自動存取子中，如下所示。  
  
 下列範例會使用多個存取子讀取及寫入工作表的 SQL Server pubs 資料庫使用多重存取子。 這是最常用的多個存取子。請參閱上述的 「 多個讀取/寫入資料列集 」 案例。  
  
 使用者記錄類別如下所示。 它會設定兩個存取子： 包含只有主要索引鍵資料行 (ID) 的存取子 0 和 1 的存取子包含其他資料行。  
  
```  
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
  
 主要的程式碼如下所示。 呼叫`MoveNext`會自動擷取資料，使用存取子 0 的主索引鍵資料行識別碼。 請注意如何**插入**方法會使用存取子 1 以避免主索引鍵資料行寫入附近。  
  
```  
int main(int argc, char* argv[])  
{  
    // Initalize COM  
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
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [使用者資料錄](../../data/oledb/user-records.md)