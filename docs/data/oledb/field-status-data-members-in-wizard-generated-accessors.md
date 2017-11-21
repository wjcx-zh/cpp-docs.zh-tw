---
title: "欄位狀態資料成員，在精靈產生的存取子中 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e3991e2e5cab8814cba4e92882fbd978bdc051eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>在精靈產生的存取子中的欄位狀態資料成員
當您使用 ATL OLE DB 消費者精靈 建立消費者時，精靈會在您指定資料行對應中每個欄位的使用者記錄類別中產生的資料成員。 每個資料成員的類型是`DWORD`並包含對應至其個別欄位的狀態值。  
  
 例如，對於資料成員*m_OwnerID*，精靈會產生額外的資料成員的欄位狀態 (*dwOwnerIDStatus*) 和另一種用於欄位長度 (*dwOwnerIDLength*). 它也會產生一個資料行對應，包含`COLUMN_ENTRY_LENGTH_STATUS`項目。  
  
 下列程式碼所示：  
  
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
>  如果您修改使用者記錄類別或撰寫自己的消費者，資料變數必須出現在狀態和長度變數之前。  
  
 您可以使用 status 值以進行偵錯。 如果 ATL OLE DB 消費者精靈產生的程式碼會產生編譯錯誤例如**DB_S_ERRORSOCCURRED**或**DB_E_ERRORSOCCURRED**，您應該先查看目前的值的欄位狀態資料成員。 具有非零值會對應至衝突的資料行。  
  
 您也可以使用 status 值來設定特定欄位的 NULL 值。 這樣可協助您在您要區分欄位值為 NULL，而不是零的情況下。 這是由您決定 NULL 是否為有效的值或特殊值，並決定您的應用程式應該如何處理它。 OLE DB 定義**DBSTATUS_S_ISNULL**指定泛型的 NULL 值的正確方法。 如果取用者讀取資料，而且值為 null，則 [狀態] 欄位會設定為**DBSTATUS_S_ISNULL**。 如果取用者想要將 NULL 值，取用者會將狀態的值設定為**DBSTATUS_S_ISNULL**之前呼叫提供者。  
  
 接下來，開啟 Oledb.h 並搜尋**DBSTATUSENUM**。 您可以再比對針對狀態則為非零的數值**DBSTATUSENUM**列舉值。 如果列舉型別名稱不足夠，告訴您是有什麼問題，請參閱 < 繫結資料值 > 一節中的 「 狀態 」 主題[OLE DB 程式設計人員指南](http://go.microsoft.com/fwlink/?linkid=121548)。 本主題包含的狀態時使用的值取得或設定資料的資料表。 長度值的相關資訊，請參閱 「 長度 」 主題，在相同的區段。  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>擷取的長度或資料行的狀態  
 您可以擷取可變長度資料行的長度或資料行的狀態 (檢查**DBSTATUS_S_ISNULL**，例如):  
  
-   若要取得長度，請使用`COLUMN_ENTRY_LENGTH`巨集。  
  
-   若要取得的狀態，請使用`COLUMN_ENTRY_STATUS`巨集。  
  
-   若要取得這兩種情況，請使用`COLUMN_ENTRY_LENGTH_STATUS`，如下所示。  
  
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
  
 當您使用`CDynamicAccessor`，長度和狀態會為您會自動繫結。 若要擷取的長度和狀態的值，請使用`GetLength`和**GetStatus**成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)