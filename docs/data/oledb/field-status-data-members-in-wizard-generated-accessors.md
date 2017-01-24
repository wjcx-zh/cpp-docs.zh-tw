---
title: "在精靈產生的存取子中的欄位狀態資料成員 | Microsoft Docs"
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
  - "OLE DB 樣板中的欄位狀態"
  - "OLE DB 消費者樣板, 欄位狀態"
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在精靈產生的存取子中的欄位狀態資料成員
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您使用 ATL OLE DB 消費者精靈建立消費者時，精靈會在使用者資料錄中，為您在資料行對應內指定的每個欄位產生資料成員。  每個資料成員都是 `DWORD` 型別，並包含了對應其個別欄位的狀態值。  
  
 例如，以 *m\_OwnerID* 資料成員而言，精靈會為欄位狀態 \(*dwOwnerIDStatus*\) 產生其他資料成員，並為欄位長度 \(*dwOwnerIDLength*\) 產生另一個資料成員。  它也會產生有 `COLUMN_ENTRY_LENGTH_STATUS` 項目的資料行對應。  
  
 請參考下列程式碼中的示範：  
  
```  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
>  如果您修改使用者資料錄類別或撰寫自己的消費者，資料變數必須出現在狀態和長度變數之前。  
  
 您可以使用狀態值來達到偵錯目的。  如果 ATL OLE DB 消費者精靈產生的程式碼產生編譯錯誤 \(例如，**DB\_S\_ERRORSOCCURRED** 或 **DB\_E\_ERRORSOCCURRED**\)，您應該先查看目前欄位狀態資料成員值。  含有非零值的欄位會對應到衝突的資料行。  
  
 您也可以使用狀態值，將特定欄位值設定為 NULL。  這樣做對於您想要分辨欄位值是 NULL 而不是零的時候相當有用。  您可以自行決定 NULL 是有效值或是特殊值，並決定應用程式應有的處理方式。  OLE DB 會定義 **DBSTATUS\_S\_ISNULL** 為指定泛用 NULL 值的正確方式。  如果消費者讀取資料而且值是 null，則該狀態欄位會設定為 **DBSTATUS\_S\_ISNULL**。  如果消費者想要設定 NULL 值，則消費者會在呼叫提供者之前將狀態值設定為 **DBSTATUS\_S\_ISNULL**。  
  
 接著，開啟 Oledb.h 並搜尋 **DBSTATUSENUM**。  然後比對非零狀態的數值和 **DBSTATUSENUM** 列舉值。  如果列舉名稱不足以告訴您哪裡有錯誤，請參閱 [OLE DB 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=121548)中＜繫結資料值＞一節的＜狀態＞主題 \(英文\)。  這個主題包含在取得或設定資料時，所使用的狀態值資料表。  如需長度值的詳細資訊，請參閱同一節中的＜長度＞主題。  
  
## 擷取資料行的長度或狀態  
 您可以擷取可變長度資料行的長度或資料行的狀態 \(例如，檢查 **DBSTATUS\_S\_ISNULL**\)：  
  
-   若要取得長度，請使用 `COLUMN_ENTRY_LENGTH` 巨集  
  
-   若要取得狀態，請使用 `COLUMN_ENTRY_STATUS` 巨集  
  
-   若要同時取得兩者，請依照下列範例所示使用 `COLUMN_ENTRY_LENGTH_STATUS`  
  
```  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts > > product;  
  
product.Open(session, "Product");  
while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
 長度和狀態會在使用 `CDynamicAccessor` 時自動繫結。  若要擷取長度和狀態值，請使用 `GetLength` 和 **GetStatus** 成員函式。  
  
## 請參閱  
 [使用 OLE DB 消費者樣板](../../data/oledb/working-with-ole-db-consumer-templates.md)