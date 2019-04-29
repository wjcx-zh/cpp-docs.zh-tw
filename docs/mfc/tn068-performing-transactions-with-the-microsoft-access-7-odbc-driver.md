---
title: TN068:使用 Microsoft Access 7 ODBC 驅動程式執行異動
ms.date: 06/28/2018
f1_keywords:
- vc.data.odbc
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
ms.openlocfilehash: 3121587f85c4ea19cc92e39569008b597d24ea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363787"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068:使用 Microsoft Access 7 ODBC 驅動程式執行異動

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本附註會說明如何使用 MFC ODBC 資料庫類別和 Microsoft Access 7.0 ODBC 驅動程式包含在 Microsoft ODBC 桌面驅動程式套件版本 3.0 時，執行交易。

## <a name="overview"></a>總覽

如果您的資料庫應用程式執行的交易，您必須呼叫小心`CDatabase::BeginTrans`和`CRecordset::Open`應用程式中正確的順序。 Microsoft Access 7.0 驅動程式會使用 Microsoft Jet 資料庫引擎，與 Jet 需要您的應用程式而不是開始上已開啟的資料指標的任何資料庫的交易。 MFC ODBC 資料庫類別中，開啟的資料指標會等於開啟`CRecordset`物件。

如果您開啟的資料錄集，然後再呼叫`BeginTrans`，您可能不會看到任何錯誤訊息。 不過，任何資料錄集更新您的應用程式會呼叫之後會變成永久`CRecordset::Update`，並更新將不會回復藉由呼叫`Rollback`。 若要避免這個問題，您必須呼叫`BeginTrans`第一次，然後開啟資料錄集。

MFC 會檢查驅動程式的功能，針對資料指標的認可和回復行為。 類別`CDatabase`提供兩個成員函式`GetCursorCommitBehavior`並`GetCursorRollbackBehavior`，以判斷在您開啟任何交易的效果`CRecordset`物件。 Microsoft Access 7.0 ODBC 驅動程式，這些成員函式會傳回`SQL_CB_CLOSE`因為 Access 驅動程式不支援資料指標保留。 因此，您必須呼叫`CRecordset::Requery`下列`CommitTrans`或`Rollback`作業。

當您需要逐一執行多個交易時，您不能呼叫`Requery`之後再啟動下一個與第一筆交易。 您必須先關閉資料錄集的下一個呼叫之前`BeginTrans`以滿足 Jet 的需求。 這個技術提示說明兩種方法可以處理這種情況：

- 在每個關閉資料錄`CommitTrans`或`Rollback`作業。

- 使用 ODBC API 函式`SQLFreeStmt`。

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>每個 CommitTrans 或復原作業之後關閉資料錄集

之前啟動交易時，請確定已關閉的資料錄集物件。 之後呼叫`BeginTrans`，呼叫資料錄集的`Open`成員函式。 關閉資料錄集後立即呼叫`CommitTrans`或`Rollback`。 請注意，重複開啟和關閉資料錄集可能會降低應用程式的效能。

## <a name="using-sqlfreestmt"></a>使用 SQLFreeStmt

您也可以使用 ODBC API 函式`SQLFreeStmt`來明確關閉資料指標之後結束交易。 若要啟動另一個交易，呼叫`BeginTrans`後面接著`CRecordset::Requery`。 當呼叫`SQLFreeStmt`，您必須指定做為第一個參數的資料錄集的 HSTMT 並*SQL_CLOSE*做為第二個參數。 這個方法是關閉及開啟資料錄集的每筆交易的開頭比更快。 下列程式碼示範如何實作這項技術：

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

// close the cursor
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

// start transaction 2
db.BeginTrans();
// now get the result set
rs.Requery();

// manipulate data

// end transaction 2
db.CommitTrans();

rs.Close();
db.Close();
```

若要實作這項技術的另一個方法是撰寫新的函式， `RequeryWithBeginTrans`，您可以呼叫它來啟動交易下, 一步 之後您認可, 或復原第一個。 若要撰寫這類函式，執行下列步驟：

1. 複製的程式碼`CRecordset::Requery( )`new 函式。

2. 若要在呼叫之後立即新增下面這一行`SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

現在您可以呼叫此函式的交易每對之間：

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> 如果您需要變更資料錄集成員變數，請勿使用這項技術*m_strFilter*或是*m_strSort*之間的交易。 在此情況下，您應該關閉資料錄集，在每個`CommitTrans`或`Rollback`作業。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
