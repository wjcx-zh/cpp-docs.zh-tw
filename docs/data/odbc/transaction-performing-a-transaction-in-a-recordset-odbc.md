---
title: 交易：執行異動中的資料錄集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 9e06d61d3d86233e136b0b3fe78f149a6778649b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035237"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>交易：執行異動中的資料錄集 (ODBC)

本主題說明如何在資料錄集執行交易。

> [!NOTE]
>  支援的只有一個層級的交易;您無法巢狀交易。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>若要在資料錄集執行交易

1. 呼叫`CDatabase`物件的`BeginTrans`成員函式。

1. 如果您未實作大量資料列擷取，呼叫`AddNew/Update`， `Edit/Update`，和`Delete`的視需要多次相同的資料庫的一或多個資料錄集物件的成員函式。 如需詳細資訊，請參閱[資料錄集：新增、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果您已實作大量資料列擷取，您必須撰寫您自己的函式來更新資料來源。

1. 最後，呼叫`CDatabase`物件的`CommitTrans`成員函式。 如果其中一種更新就會發生錯誤，或您選擇取消所做的變更，請呼叫其`Rollback`成員函式。

下列範例會使用兩個資料錄集，從學校的註冊資料庫，移除所有的學生已註冊的類別中的學生刪除某學生的註冊。 因為`Delete`中這兩個資料錄集的呼叫都必須成功，交易就需要。 此範例假設存在`m_dbStudentReg`，類型的成員變數`CDatabase`已經連接到資料來源和資料錄集類別`CEnrollmentSet`和`CStudentSet`。 `strStudentID`變數包含值，從使用者處取得。

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
>  呼叫`BeginTrans`而不呼叫一次`CommitTrans`或`Rollback`時發生。

## <a name="see-also"></a>另請參閱

[異動 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[交易：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)