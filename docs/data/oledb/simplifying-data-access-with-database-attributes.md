---
title: "以資料庫屬性簡化資料存取 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "屬性 [C++], 資料存取"
  - "屬性 [C++], 資料庫"
  - "屬性 [C++], OLE DB 消費者"
  - "資料 [C++], 簡化存取"
  - "資料存取 [C++], 資料庫屬性"
  - "資料庫屬性 [C++]"
  - "資料庫 [C++], 屬性"
  - "OLE DB 消費者 [C++], 資料庫屬性"
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 以資料庫屬性簡化資料存取
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會示範使用資料庫屬性以簡化資料庫作業的方式。  
  
 存取資料庫資訊的基本方法，是為資料庫中特定的資料表建立命令 \(或資料表\) 類別和使用者資料錄類別。  資料庫屬性可以簡化某些您先前必須做的樣板宣告。  
  
 為了示範資料庫屬性的用法，下列章節會顯示兩個相同的資料表和使用者資料錄類別宣告：第一個使用屬性，第二個則使用 OLE DB 樣板。  這種宣告程式碼通常放置在為資料表或命令物件命名的標頭檔中，例如，Authors.h。  
  
 比較兩個檔案，您會發現使用屬性有多簡單。  其中的差異是：  
  
-   使用屬性時，您只需要宣告一個類別：`CAuthors`，而使用樣板時，則必須宣告兩個類別：`CAuthorsNoAttrAccessor` 和 `CAuthorsNoAttr`。  
  
-   在屬性化版本中的 `db_source` 呼叫與樣板宣告中的 `OpenDataSource()` 呼叫相同。  
  
-   屬性化版本中的 **db\_table** 呼叫與下列樣板宣告的呼叫相同：  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
    ```  
  
-   在屬性化版本中的 **db\_column** 呼叫與樣板宣告的資料行對應 \(請參閱 `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`\) 相同。  
  
 這種屬性會為您插入使用者資料錄類別宣告。  使用者資料錄類別與樣板宣告中的 `CAuthorsNoAttrAccessor` 相同。  如果您的資料表類別是 `CAuthors`，插入的使用者資料錄類別就會命名為 `CAuthorsAccessor`，且您只能在插入程式碼中檢視它的宣告。  如需詳細資訊，請參閱[使用者資料錄](../../data/oledb/user-records.md)中的「插入屬性的使用者資料錄類別」。  
  
 請注意，您必須在屬性化和樣板化的程式碼中，使用 `CDBPropSet::AddProperty` 設定資料列集屬性。  
  
 如需本主題探討的屬性的詳細資訊，請參閱 [OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)。  
  
## 使用屬性的資料表和存取子宣告  
 下列程式碼會在資料表類別上呼叫 `db_source` 和 **db\_table**。  `db_source` 可以指定要使用的資料來源和連接。  **db\_table** 可以插入適當的樣板程式碼，以便宣告資料表類別。  **db\_column** 可以指定資料行對應和插入存取子宣告。  您可在支援 ATL 的任何專案內使用 OLE DB 消費者屬性。  
  
 以下是使用屬性的資料表和存取子宣告：  
  
```  
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
  
## 使用樣板的資料表和存取子宣告  
 以下是使用樣板的資料表和存取子宣告。  
  
```  
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
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
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
  
## 請參閱  
 [OLE DB Consumer Attributes](../../windows/ole-db-consumer-attributes.md)   
 [Attributes Walkthroughs](http://msdn.microsoft.com/zh-tw/73df1d5d-261a-4521-98fb-06dcbf5ec0d0)