---
title: 異動：在一個資料錄集內執行異動 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 94177a27a1f99a8c9c37b7fce3f697fd0088b7c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212585"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>異動：在一個資料錄集內執行異動 (ODBC)

本主題說明如何在記錄集中執行交易。

> [!NOTE]
>  僅支援一個層級的交易;您無法嵌套交易。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>若要在記錄集中執行交易

1. 呼叫 `CDatabase` 物件的 `BeginTrans` 成員函式。

1. 如果您尚未執行大量資料列提取，請視需要呼叫相同資料庫的一個或多個 recordset 物件的 `AddNew/Update`、`Edit/Update`和 `Delete` 成員函式。 如需詳細資訊，請參閱[記錄集：加入、更新和刪除記錄（ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果您已實作用大量資料列提取，您必須撰寫自己的函式來更新資料來源。

1. 最後，呼叫 `CDatabase` 物件的 `CommitTrans` 成員函式。 如果其中一個更新發生錯誤，或您決定取消變更，請呼叫其 `Rollback` 成員函式。

下列範例會使用兩個記錄集，從學校註冊資料庫中刪除學生的註冊，並從註冊學生的所有課程中移除學生。 因為兩個記錄集中的 `Delete` 呼叫都必須成功，所以需要交易。 這個範例假設存在 `m_dbStudentReg`、類型的成員變數 `CDatabase` 已經連接到資料來源，以及記錄集類別 `CEnrollmentSet` 和 `CStudentSet`。 `strStudentID` 變數包含從使用者取得的值。

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
>  再次呼叫 `BeginTrans`，而不呼叫 `CommitTrans` 或 `Rollback` 是錯誤。

## <a name="see-also"></a>另請參閱

[異動 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
