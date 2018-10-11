---
title: 欄位狀態資料成員，在精靈產生存取子中的 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b1c48f4699c0add937c2bcdb13d49bce8cb895c4
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083955"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>在精靈產生的存取子中的欄位狀態資料成員

當您使用 [ATL OLE DB 消費者精靈] 建立消費者時，精靈會在您指定資料行對應中的每個欄位的使用者記錄類別中產生資料成員。 每個資料成員的類型是`DWORD`並包含對應至其個別欄位的狀態值。  
  
例如，對於資料成員*m_OwnerID*，精靈會產生額外的資料成員的欄位狀態 (*dwOwnerIDStatus*)，另一個則欄位長度 (*dwOwnerIDLength*). 它也會產生資料行對應與 COLUMN_ENTRY_LENGTH_STATUS 項。  
  
這是由下列程式碼所示：  
  
```cpp  
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
  
您可以使用 [狀態] 值，以進行偵錯。 如果 ATL OLE DB 消費者精靈產生的程式碼會產生編譯錯誤，例如 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED，您應該先查看欄位狀態資料成員的目前值。 具有非零的值會對應至衝突的資料行。  
  
您也可以使用 [狀態] 值來設定特定欄位的 NULL 值。 這樣可協助您的情況下您想用來區別欄位值為 NULL，而不是零。 它是您必須決定 NULL 是否為有效的值或特殊值，並決定您的應用程式應該如何處理它。 OLE DB 定義為 DBSTATUS_S_ISNULL 指定泛用的 NULL 值的正確方法。 如果取用者讀取資料，此值為 null，會將 [狀態] 欄位設為 DBSTATUS_S_ISNULL。 如果取用者想要設定為 NULL 值，取用者狀態值設定為 DBSTATUS_S_ISNULL 之前呼叫提供者。  
  
接下來，開啟 Oledb.h 並搜尋`DBSTATUSENUM`。 您可以接著比對的非零值的狀態，針對數值`DBSTATUSENUM`列舉值。 如果列舉名稱不足以告訴您哪裡有錯誤，請參閱 < 繫結資料值 > 一節中的 「 狀態 」 主題[OLE DB 程式設計人員指南](/previous-versions/windows/desktop/ms713643)。 本主題包含的狀態時使用的值取得或設定資料的資料表。 長度值的詳細資訊，請參閱 「 長度 」 主題中的相同區段。  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>擷取的長度或資料行的狀態  

您可以擷取可變長度資料行的長度或資料行 （例如檢查 DBSTATUS_S_ISNULL，） 的狀態：  
  
- 若要取得長度，請使用 COLUMN_ENTRY_LENGTH 巨集。  
  
- 若要取得狀態，請使用 COLUMN_ENTRY_STATUS 巨集。  
  
- 若要取得這兩個，請使用 COLUMN_ENTRY_LENGTH_STATUS，，如下所示。  
  
```cpp  
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
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
當您使用`CDynamicAccessor`，長度和狀態會為您會自動繫結。 若要擷取的長度和狀態的值，請使用`GetLength`和`GetStatus`成員函式。  
  
## <a name="see-also"></a>另請參閱  

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)