---
title: 異動：在一個資料錄集內執行異動 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358087"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>異動：在一個資料錄集內執行異動 (ODBC)

本主題介紹如何在記錄集中執行事務。

> [!NOTE]
> 僅支援一個級別的事務;不能嵌套事務。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>記錄集中執行事務

1. 調用`CDatabase``BeginTrans`對象的成員函數。

1. 如果尚未實現批量行提取,請根據需要多次調用同`AddNew/Update``Edit/Update`一資料庫`Delete`的一個或多個記錄集物件的 的和的成員函數。 有關詳細資訊,請參閱[記錄集:添加、更新和刪除記錄 (ODBC)。](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) 如果已實現批量行提取,則必須編寫自己的函數來更新數據源。

1. 最後,`CDatabase`調用`CommitTrans`對象的成員函數。 如果其中一個更新中出現錯誤,或者您決定取消更改,請呼叫其成員`Rollback`函數。

下面的示例使用兩個記錄集從學校註冊資料庫中刪除學生的註冊,從註冊學生的所有班級中刪除該學生。 由於兩`Delete`個記錄集中的調用必須成功,因此需要事務。 此範例的識別碼`m_dbStudentReg`存在 ,類型`CDatabase`的成員變數已連接到資料來源,以及紀錄集`CEnrollmentSet`類別`CStudentSet`與 。 該`strStudentID`變數包含從用戶獲取的值。

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
> 再次`BeginTrans`調用而不調`CommitTrans`用`Rollback`或 是一個錯誤。

## <a name="see-also"></a>另請參閱

[異動 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
