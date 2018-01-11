---
title: "異動： 執行交易集中的資料錄 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd412549c86c3ca8ddc004016183b64248bdf292
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>異動：在一個資料錄集內執行異動 (ODBC)
本主題說明如何在資料錄集執行交易。  
  
> [!NOTE]
>  只有一個層級的交易支援。您無法巢狀交易。  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>若要執行交易集中的資料錄  
  
1.  呼叫`CDatabase`物件的**BeginTrans**成員函式。  
  
2.  如果您未實作大量資料列擷取，呼叫**AddNew/更新**，**編輯/更新**，和**刪除**相同的一或多個資料錄集物件的成員函式資料庫所需的次數。 如需詳細資訊，請參閱[資料錄集： 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果您已實作大量資料列擷取，您必須撰寫您自己的函式來更新資料來源。  
  
3.  最後，呼叫`CDatabase`物件的**CommitTrans**成員函式。 如果其中一個更新中發生錯誤，或您決定要取消的變更，請呼叫其**復原**成員函式。  
  
 下列範例會使用兩個資料錄集，一位學生註冊刪除學校註冊資料庫，移除從學生已註冊的所有類別。 因為**刪除**中這兩個資料錄集的呼叫都必須成功，必須指定交易。 此範例假設存在`m_dbStudentReg`，類型的成員變數`CDatabase`已經連接到資料來源和資料錄集類別`CEnrollmentSet`和`CStudentSet`。 `strStudentID`變數包含從使用者取得的值。  
  
```  
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )  
{  
    // remove student from all the classes  
    // the student is enrolled in  
  
    if ( !m_dbStudentReg.BeginTrans( ) )  
        return FALSE;  
  
    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);  
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    CStudentSet rsStudentSet(&m_dbStudentReg);  
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsStudentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    TRY  
    {  
        while ( !rsEnrollmentSet.IsEOF( ) )  
        {  
            rsEnrollmentSet.Delete( );  
            rsEnrollmentSet.MoveNext( );  
        }  
  
        // delete the student record  
        rsStudentSet.Delete( );  
  
        m_dbStudentReg.CommitTrans( );  
    }  
  
    CATCH_ALL(e)  
    {  
        m_dbStudentReg.Rollback( );  
        return FALSE;  
    }  
    END_CATCH_ALL  
  
    rsEnrollmentSet.Close( );  
    rsStudentSet.Close( );  
  
    return TRUE;  
  
}  
```  
  
> [!NOTE]
>  呼叫**BeginTrans**一次而不需呼叫**CommitTrans**或**復原**是錯誤。  
  
## <a name="see-also"></a>請參閱  
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [異動： 異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)