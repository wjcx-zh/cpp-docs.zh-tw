---
title: "以資料庫屬性簡化資料存取 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18ec902d3b9defc57c10a08b436393a48091e749
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="simplifying-data-access-with-database-attributes"></a>以資料庫屬性簡化資料存取
本主題示範如何使用資料庫屬性，以簡化資料庫作業。  
  
 從資料庫存取資訊的基本方法是在資料庫中建立的命令 （或資料表） 類別和特定資料表的使用者記錄類別。 資料庫屬性簡化部分您先前必須做的樣板宣告。  
  
 若要示範如何使用資料庫屬性，下列各節會顯示兩個相同的資料表和使用者記錄類別宣告： 第一個使用屬性，第二個使用 OLE DB 樣板。 這類宣告程式碼通常位於標頭檔，為資料表或命令物件，例如 Authors.h。  
  
 藉由比較兩個檔案，您可以看到這是使用屬性有多麼簡單。 其中的差異是：  
  
-   使用屬性，您只需要宣告一個類別： `CAuthors`，而您必須使用樣板宣告兩個：`CAuthorsNoAttrAccessor`和`CAuthorsNoAttr`。  
  
-   `db_source`呼叫屬性化的版本中是相當於`OpenDataSource()`呼叫樣板宣告中。  
  
-   **Db_table**呼叫屬性化的版本中是相當於下列的樣板宣告：  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
    ```  
  
-   **Db_column**呼叫屬性化的版本中都相當於資料行對應 (請參閱`BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) 樣板宣告中。  
  
 屬性會為您插入使用者記錄類別宣告。 使用者記錄類別相當於`CAuthorsNoAttrAccessor`樣板宣告中。 如果資料表類別`CAuthors`，插入的使用者記錄類別的名稱為`CAuthorsAccessor`，您只可以檢視其宣告中插入的程式碼。 如需詳細資訊，請參閱 < 插入屬性使用者記錄類別 」[使用者資料錄](../../data/oledb/user-records.md)。  
  
 請注意，在屬性化和樣板化程式碼，您必須設定使用的資料列集屬性`CDBPropSet::AddProperty`。  
  
 本主題所討論的屬性相關資訊，請參閱[OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)。  
  
## <a name="table-and-accessor-declaration-using-attributes"></a>使用資料表和存取子宣告屬性  
 下列程式碼會呼叫`db_source`和**db_table**資料表類別上。 `db_source` 指定要使用的連接與資料來源。 **db_table**會將適當的範本程式碼，來宣告資料表類別。 **db_column**指定資料行對應，以及將存取子宣告。 您可以在任何支援 ATL 的專案中使用 OLE DB 消費者屬性  
  
 以下是使用屬性的資料表和存取子宣告：  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// Table and accessor declaration using attributes  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// Table class declaration  
// (Note that you must provide your own connection string for db_source.)  
[  
   db_source(L"your connection string"),  
   db_table("Authors")  
]  
class CAuthors  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## <a name="table-and-accessor-declaration-using-templates"></a>使用資料表和存取子宣告範本  
 以下是使用範本的資料表和存取子宣告。  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// Table and user record class declaration using templates  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// User record class declaration  
class CAuthorsNoAttrAccessor  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   LONG m_AuID;  
   TCHAR m_Author[51];  
   SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
   HRESULT OpenDataSource()  
   {  
      CDataSource _db;  

HRESULT hr;  
      hr = _db.OpenFromInitializationString(L"your connection string");  
      if (FAILED(hr))  
      {  
#ifdef _DEBUG  
         AtlTraceErrorRecords(hr);  
#endif  
         return hr;  
      }  
      return m_session.Open(_db);  
   }  
   void CloseDataSource()  
   {  
      m_session.Close();  
   }  
   operator const CSession&()  
   {  
      return m_session;  
   }  
   CSession m_session;  
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)  
   END_COLUMN_MAP()  
};  
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
{  
public:  
   HRESULT OpenAll()  
   {  
HRESULT hr;  
      hr = OpenDataSource();  
      if (FAILED(hr))  
         return hr;  
      __if_exists(GetRowsetProperties)  
      {  
         CDBPropSet propset(DBPROPSET_ROWSET);  
         __if_exists(HasBookmark)  
         {  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
         }  
         GetRowsetProperties(&propset);  
         return OpenRowset(&propset);  
      }  
      __if_not_exists(GetRowsetProperties)  
      {  
         __if_exists(HasBookmark)  
         {  
            CDBPropSet propset(DBPROPSET_ROWSET);  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
            return OpenRowset(&propset);  
         }  
      }  
      return OpenRowset();  
   }  
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
   {  
HRESULT hr = Open(m_session, "Authors", pPropSet);  
#ifdef _DEBUG  
      if(FAILED(hr))  
         AtlTraceErrorRecords(hr);  
#endif  
      return hr;  
   }  
   void CloseAll()  
   {  
      Close();  
      CloseDataSource();  
   }  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)   
 [屬性的逐步解說](http://msdn.microsoft.com/en-us/73df1d5d-261a-4521-98fb-06dcbf5ec0d0)