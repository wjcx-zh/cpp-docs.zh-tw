---
title: "異動：在一個資料錄集內執行異動 (ODBC) | Microsoft Docs"
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
  - "異動, 更新資料錄集"
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 異動：在一個資料錄集內執行異動 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何在一個資料錄集內執行交易。  
  
> [!NOTE]
>  只支援單層交易，您不能使用巢狀交易。  
  
#### 若要在資料錄集內執行交易  
  
1.  呼叫 `CDatabase` 物件的 **BeginTrans** 成員函式。  
  
2.  若您沒有實作大量資料列擷取，則需要多次呼叫相同資料庫內一個或多個資料錄集物件的 **AddNew\/Update**、**Edit\/Update** 和 **Delete** 成員函式。  如需詳細資訊，請參閱[資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。  若您有實作大量資料列擷取，您必須撰寫您自己的函式以更新資料來源。  
  
3.  最後，呼叫 `CDatabase` 物件的 **CommitTrans** 成員函式。  如果其中一個更新發生錯誤，或您決定取消此變更，請呼叫其 **Rollback** 成員函式。  
  
 以下的範例使用兩個資料錄集以便從學校的註冊資料庫中刪除學生的入學登記，從所有類別中移除已入學的學生。  因為在兩個資料錄集中的 **Delete** 呼叫都必須成功，所以需要一筆交易。  範例會假設已存在有連結至資料來源的 `CDatabase` 型別的成員變數 \(Member Variable\) `m_dbStudentReg` 以及資料錄類別 `CEnrollmentSet` 和 `CStudentSet`。  `strStudentID` 變數包含自使用者取得的值。  
  
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
>  再次呼叫 **BeginTrans** 卻沒有呼叫 **CommitTrans** 或 **Rollback** 是個錯誤。  
  
## 請參閱  
 [異動 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [異動：異動如何影響更新 \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)