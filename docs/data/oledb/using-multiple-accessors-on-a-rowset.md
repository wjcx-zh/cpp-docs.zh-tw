---
title: "在資料列集上使用多重存取子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取子 [C++], 資料列集"
  - "BEGIN_ACCESSOR 巨集"
  - "BEGIN_ACCESSOR 巨集, 多個存取子"
  - "資料列集 [C++], 多個存取子"
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在資料列集上使用多重存取子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列是需要使用多重存取子的三種基本案例：  
  
-   **多重讀取\/寫入資料列集。**在此案例中，您擁有一個包含主索引鍵的資料表。  您想要能夠讀取資料列內的所有資料行，包括了主索引鍵。  您也想要將資料寫入主索引鍵以外的所有資料行內 \(因為您無法寫入主索引鍵資料行\)。  在此案例中，您要設定兩個存取子：  
  
    -   包含所有資料行的存取子 0。  
  
    -   包含所有在主索引鍵以外資料行的存取子 1。  
  
-   **效能**在此案例中，一或多個資料行包含了大量的資料，例如圖形、音效或視訊檔。  每次您移到一資料列，應該就不希望再擷取內含大型資料檔的資料行，因為這樣做會降低應用程式的效能。  
  
     您可以分別設定存取子，其中的第一個存取子包含了內含大型資料資料行以外的所有資料行，且可以自動地擷取這些資料行的資料；這就是自動存取子。  第二個存取子只可以擷取包含大型資料的資料行，不過它並不會自動地從這些資料行擷取資料。  您可使用其他方法在需要時更新或擷取大型資料。  
  
    -   存取子 0 為自動存取子，它可擷取所有資料行 \(除了大型資料的資料行以外\)。  
  
    -   存取子 1 並非自動存取子，它可擷取包含大型資料的資料行。  
  
     使用自動引數來指定存取子是否為自動存取子。  
  
-   **多重 ISequentialStream 資料行。**在此案例中，您擁有一個以上包含 `ISequentialStream` 資料的資料行。  不過，每個存取子只限於一個 `ISequentialStream` 資料流。  若要解決此問題，請設定多個存取子，每個都包含一 `ISequentialStream` 指標。  
  
 您通常使用 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../../data/oledb/end-accessor.md) 巨集來建立存取子。  您也可使用 [db\_accessor](../../windows/db-accessor.md) 屬性\(存取子將進一步描述於[使用者資料錄](../../data/oledb/user-records.md)內\)。巨集或屬性指定了存取子是否為自動或非自動存取子：  
  
-   在自動存取子內，移動方法例如 **MoveFirst**、`MoveLast`、`MoveNext` 和 `MovePrev`，將會自動為所有指定的資料行擷取資料。  存取子 0 應該屬於自動存取子。  
  
-   在非自動存取子內，擷取只會在您明確地呼叫 **Update**、**Insert**、**Fetch** 或 **Delete** 等方法時發生。  在上述案例中，您可能不希望每次移動時都擷取所有的資料行。  您可將一個或多個資料行放在個別的存取子內，並讓它成為非自動存取子，如下所示。  
  
 底下的範例會使用多重存取子來讀取與寫入至使用多重存取子的 SQL Server 中 pubs 資料庫的 jobs 資料表內。  這是最常見的多重存取子用法，請參閱上方的「多重讀取\/寫入資料列集」案例。  
  
 使用者資料錄類別將如下所示。  它會設定兩個存取子：只包含主索引鍵資料行 \(ID\) 的存取子 0 以及包含其他資料行的存取子 1。  
  
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
  
 主程式碼如下。  呼叫 `MoveNext` 可自動使用存取子 0 從主索引鍵資料行 ID 擷取資料。  請注意靠近結尾的 **Insert** 方法如何使用存取子 1 來避免寫入主索引鍵資料行。  
  
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
            CTable<CAccessor<CJobs> > jobs;  
  
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
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [使用者資料錄](../../data/oledb/user-records.md)