---
title: "資料錄集：宣告預先定義查詢的類別 (ODBC) | Microsoft Docs"
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
  - "ODBC 資料錄集, 查詢"
  - "預先定義的查詢和資料錄集"
  - "資料錄集, 預先定義的查詢"
  - "資料錄集, 預存程序"
  - "預存程序, 和資料錄集"
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄集：宣告預先定義查詢的類別 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 本主題說明如何建立預先定義查詢的資料錄集類別 \(有時稱為預存程序 \(Stored Procedure\)，例如在 Microsoft SQL Server 中\)。  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  若已實作大量資料列擷取，則此過程會非常相似。  若要了解實作與未實作大量資料列擷取的資料錄集之間的差異，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 某些資料庫管理系統 \(DBMS\) 可讓您建立預先定義詢，並允許您從應用程式中以函式方式呼叫此查詢。  查詢具有名稱，可能有參數，且有可能會傳回資料錄。  本主題中的程序會說明如何呼叫可傳回資料錄的預先定義查詢 \(且可能接受參數\)。  
  
 資料庫類別不支援更新預先定義查詢。  快照集預先定義查詢與動態集預先定義查詢間的差異不是在於更新能力，而是在於您的資料錄集可否看到其他人 \(或您的程式中的其他資料錄集\) 所做的變動。  
  
> [!TIP]
>  您並不需要資料錄集呼叫不傳回資料錄的預先定義查詢。  依照下列的說明準備 SQL 陳述式，但藉由呼叫 `CDatabase` 的 [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 成員函式來執行。  
  
 您可建立單一資料錄集類別來管理預先定義查詢的呼叫，但您必須自己做某些工作。  精靈並不支援特別為這個目的而建立類別。  
  
#### 若要建立一個呼叫預先定義查詢 \(預存程序\) 的類別  
  
1.  使用 \[加入類別\] 的 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)，來建立資料表 \(具有查詢所傳回的最多資料行\) 的資料錄集類別。  如此您便可了解開頭出發點。  
  
2.  為任何資料表的任何資料行 \(查詢所傳回的\) 手動加入精靈沒有為您建立的資料成員。  
  
     例如，查詢若是傳回三個資料行且每一個都是來自兩個附加的資料表內，就要在類別中加入六個欄位資料成員 \(適當的資料型別\)。  
  
3.  在類別的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成員函式中，手動加入 [RFX](../../data/odbc/record-field-exchange-rfx.md) 函式呼叫，每個加入的欄位資料成員的資料型別都要對應至一個函式呼叫。  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  您必須知道結果集 \(Result Set\) 中傳回的資料型別和資料行順序。  `DoFieldExchange` 內 RFX 函式呼叫的順序必須符合結果集資料行的順序。  
  
4.  在資料錄集類別建構函式中手動加入新欄位資料成員的初始化。  
  
     您也必須遞增 [m\_nFields](../Topic/CRecordset::m_nFields.md) 資料成員的初始化數值。  精靈雖會編寫初始化，但其只涵蓋其為您加入的欄位資料成員。  例如：  
  
    ```  
    m_nFields += 6;  
    ```  
  
     某些資料型別不該在這裡初始化，例如 `CLongBinary` 或位元組陣列。  
  
5.  查詢若可接受參數，便要為每個參數加入一個參數資料成員、RFX 函式呼叫和個別的初始化。  
  
6.  您必須增加每個加入參數的 `m_nParams`，就如同您在本程序的步驟 4 中，為加入欄位所做的 `m_nFields`。  如需詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
7.  依照下列形式，手動編寫一個 SQL 陳述式字串：  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     其中 **CALL** 是一個 ODBC 關鍵字，**proc\-name** 是一個已知在資料來源上的查詢名稱，而 "?" 項目是您在執行階段提供給資料錄集的參數值之替代符號 \(如果有的話\)。  下列範例為一個參數準備一個替代符號：  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  在開啟資料錄集的程式碼中，設定資料錄集的參數資料成員值，再呼叫 **Open** 成員函式，然後傳遞 **lpszSQL** 參數的 SQL 字串。  或者取代您的類別中 `GetDefaultSQL` 成員函式所傳回的字串。  
  
 下列範例示範呼叫預先定義查詢 \(名為 `Delinquent_Accts`\) 的程序，此查詢接受一個銷售地區號碼的參數。  這個查詢會傳回三個資料行：`Acct_No`、`L_Name`、`Phone`。  所有的資料行都是來自 Customers 資料表。  
  
 下面資料錄集為查詢所傳回的資料行指定了欄位資料成員，以及執行階段時要求的銷售地區號碼參數。  
  
```  
class CDelinquents : public CRecordset  
{  
// Field/Param Data  
    LONG m_lAcct_No;  
    CString m_strL_Name;  
    CString m_strPhone;  
    LONG m_lDistParam;  
    // ...  
};  
```  
  
 這個類別宣告除了手動加入的 `m_lDistParam` 成員以外，其餘皆與精靈編寫的相同。  其他的成員並未顯示在此。  
  
 下一個範例會說明 `CDelinquents` 建構函式內的資料成員初始化。  
  
```  
CDelinquents::CDelinquents(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
    // Wizard-generated params:  
    m_lAcct_No = 0;  
    m_strL_Name = "";  
    m_strPhone = "";  
    m_nFields = 3;  
    // User-defined params:  
    m_nParams = 1;  
    m_lDistParam = 0;  
}  
```  
  
 請注意 [m\_nFields](../Topic/CRecordset::m_nFields.md) 和 [m\_nParams](../Topic/CRecordset::m_nParams.md) 的初始化。  精靈會將 `m_nFields` 初始化；您要自己將 `m_nParams` 初始化。  
  
 下一個範例會說明 `CDelinquents::DoFieldExchange` 內的 RFX 函式：  
  
```  
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Long(pFX, "Acct_No", m_lAcct_No);  
    RFX_Text(pFX, "L_Name", m_strL_Name);  
    RFX_Text(pFX, "Phone", m_strPhone);  
    pFX->SetFieldType(CFieldExchange::param);  
    RFX_Long(pFX, "Dist_No", m_lDistParam);  
}  
```  
  
 除了為三個傳回的資料行建立 RFX 呼叫外，此程式碼會管理繫結您在執行階段傳入的參數。  這個參數是 `Dist_No` \(地區號碼\) 資料行的索引鍵。  
  
 下一個範例說明如何設定 SQL 字串和如何使用它來開啟資料錄集。  
  
```  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
 此程式碼會建構一個快照集，傳遞一個先前從使用者那裡取得的參數並呼叫預先定義查詢。  當查詢執行時，它會為指定的銷售地區傳回資料錄。  每個資料錄包含有帳戶號碼、客戶的姓氏和客戶的電話號碼的資料行。  
  
> [!TIP]
>  您可能會想處理來自預存程序的傳回值 \(輸出參數\)。  如需詳細資訊和範例，請參閱 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：重新查詢資料錄集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [資料錄集：宣告資料表的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)