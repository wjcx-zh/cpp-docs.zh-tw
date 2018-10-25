---
title: 異動： 在資料錄集 (ODBC) 中執行的交易 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9d8075cd0d2f339db255f669386b888a3f11dd6a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073612"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>異動：在一個資料錄集內執行異動 (ODBC)

本主題說明如何在資料錄集執行交易。

> [!NOTE]
>  支援的只有一個層級的交易;您無法巢狀交易。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>若要在資料錄集執行交易

1. 呼叫`CDatabase`物件的`BeginTrans`成員函式。

1. 如果您未實作大量資料列擷取，呼叫`AddNew/Update`， `Edit/Update`，和`Delete`的視需要多次相同的資料庫的一或多個資料錄集物件的成員函式。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果您已實作大量資料列擷取，您必須撰寫您自己的函式來更新資料來源。

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
[異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)