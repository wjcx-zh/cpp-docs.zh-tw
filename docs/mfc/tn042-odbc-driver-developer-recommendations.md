---
title: TN042：ODBC 驅動程式開發人員建議
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372142"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042：ODBC 驅動程式開發人員建議

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明介紹了 ODBC 驅動程式編寫器的指南。 它概述了 MFC 資料庫類對 ODBC 功能的一般要求和假設,以及各種預期的語義詳細資訊。 介紹了支援`CRecordset`三種打開模式(**僅轉發**、**快照**和**動態集**)所需的驅動程式功能。

## <a name="odbcs-cursor-library"></a>ODBC 的游標庫

MFC 資料庫類向使用者提供的功能在許多情況下超過了大多數級別 1 ODBC 驅動程式提供的功能。 幸運的是,ODBC 的游標庫將在資料庫類和驅動程序之間分層,並自動提供大部分附加功能。

例如,大多數 1.0 驅動程式不支援向後滾動。 游標庫可以檢測到這一點,並將緩存驅動程式中的行,並在中的`SQLExtendedFetch`FETCH_PREV調用時根據需要顯示它們。

游標庫依賴的另一個重要示例是定位更新。 大多數 1.0 驅動程式也沒有定位更新,但游標庫將生成更新語句,這些語句根據數據源的當前緩存數據值或緩存的時間戳值標識目標行。

類庫從不使用多個行集。 因此,少數`SQLSetPos`語句始終應用於行集的第 1 行。

## <a name="cdatabases"></a>C 資料庫

每個`CDatabase`分配一個**HDBC。** (如果使用`CDatabase`'s`ExecuteSQL`函數 ,則臨時分配**HSTMT。** 因此,如果需要`CDatabase`多個 HDBC,則必須支援每個**HENV**的多個**HDBC。**

資料庫類需要游標庫。 這反映在`SQLSetConnections`**電話SQL_ODBC_CURSORS,SQL_CUR_USE_ODBC。** **SQL_CUR_USE_ODBC**

`SQLDriverConnect`**SQL_DRIVER_COMPLETE**用於`CDatabase::Open`建立與數據源的連接。

司機`SQLGetInfo SQL_ODBC_API_CONFORMANCE` >= 必須支援**SQL_OAC_LEVEL1,SQL_OSC_MINIMUM。** `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**

`CDatabase`為了支援 及其從屬記錄集`SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR`的 事務 **,SQL_CURSOR_ROLLBACK_BEHAVIOR**必須具有**SQL_CR_PRESERVE**。 否則,將忽略執行事務控制件的嘗試。

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`必須支援。 如果它返回"Y",則對數據源不執行任何更新操作。

開啟`CDatabase`ReadOnly,則嘗試設定僅讀的資料來源會`SQLSetConnectOption SQL_ACCESS_MODE`使用**SQL_MODE_READ_ONLY**。

如果標識符需要報價,則應從`SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR`具有呼叫的驅動程式返回此資訊。

出於調試目的,`SQLGetInfo SQL_DBMS_VER`並從驅動程式中檢索**SQL_DBMS_NAME。**

`SQLSetStmtOption SQL_QUERY_TIMEOUT`**和SQL_ASYNC_ENABLE**可以調用`CDatabase`的**HDBC。**

`SQLError`可以使用任何或所有參數 NULL 呼叫。

`SQLAllocEnv`當然,`SQLAllocConnect``SQLDisconnect``SQLFreeConnect`和必須支援。

## <a name="executesql"></a>ExecuteSQL

除了分配與釋放臨時**HSTMT**`ExecuteSQL``SQLExecDirect``SQLFetch`外,`SQLNumResultCol``SQLMoreResults`呼叫與 。 `SQLCancel`可呼叫**HSTMT**。

## <a name="getdatabasename"></a>取得資料庫名稱

`SQLGetInfo SQL_DATABASE_NAME`將被調用。

## <a name="begintrans-committrans-rollback"></a>開始轉換、提交轉換、回滾

`SQLSetConnectOption SQL_AUTOCOMMIT`和`SQLTransact SQL_COMMIT`,如果發出事務請求,將調用**SQL_ROLLBACK**和**SQL_AUTOCOMMIT。**

## <a name="crecordsets"></a>C 記錄集

`SQLAllocStmt``SQLPrepare` `Open``SQLFreeStmt`(對於更新操作) 必須支援。 `SQLExecute` `Requery` `SQLExecDirect` `SQLNumResultCols`並將`SQLDescribeCol`調用不同時間設置的結果。

`SQLSetParam`廣泛用於綁定參數數據和**DATA_AT_EXEC**功能。

`SQLBindCol`廣泛用於將輸出列數據存儲位置與ODBC註冊。

兩`SQLGetData`個調用用於檢索**SQL_LONG_VARCHAR**和**SQL_LONG_VARBINARY**數據。 第一個調用嘗試通過使用 cbMaxValue 0`SQLGetData`調用 ,但使用有效的 pcbValue 來查找列值的總長度。 如果 pcbValue 持有**SQL_NO_TOTAL**,則引發異常。 否則,將分配**HGLOBAL,** 並`SQLGetData`調用 另一個調用來檢索整個結果。

## <a name="updating"></a>Updating

如果請求悲觀鎖定,`SQLGetInfo SQL_LOCK_TYPES`將查詢。 如果**不支援SQL_LCK_EXCLUSIVE,** 將引發異常。

`CRecordset`嘗試更新 (**快照**或**動態集**) 將導致分配第二個**HSTMT。** 對於不支援第二個**HSTMT**的驅動程式,游標庫將類比此功能。 遺憾的是,這有時可能意味著在處理第二個**HSTMT**請求之前強制第一個**HSTMT**上的當前查詢完成。

`SQLFreeStmt SQL_CLOSE`**和SQL_RESET_PARAMS,**`SQLGetCursorName`將在更新操作期間調用。

如果**輸出列**中有**CLongBinarys,** 則必須支援 ODBC **DATA_AT_EXEC**功能。 這包括從`SQLExecDirect`返回`SQLParamData`**SQL_NEED_DATA**`SQLPutData`與 。

`SQLRowCount`在執行後調用,以驗證`SQLExecDirect`只有 1 條記錄由 更新。

## <a name="forwardonly-cursors"></a>只轉寄游標

操作`SQLFetch`只是必要`Move`的 。 請注意,**僅轉發**游標不支援更新。

## <a name="snapshot-cursors"></a>快照游標

快照功能需要`SQLExtendedFetch`支援。 如上所述,ODBC 游標庫將檢測驅動程式何時不`SQLExtendedFetch`支援 ,並本身提供必要的支援。

`SQLGetInfo`**,SQL_SCROLL_OPTIONS**必須支援**SQL_SO_STATIC**。

## <a name="dynaset-cursors"></a>發電機游標

以下是開啟動態集所需的最低支援:

`SQLGetInfo`**,SQL_ODBC_VER**必須返回>"01"。

`SQLGetInfo`**,SQL_SCROLL_OPTIONS**必須支援**SQL_SO_KEYSET_DRIVEN。**

`SQLGetInfo`**,SQL_ROW_UPDATES**必須返回"Y"。

`SQLGetInfo`**,SQL_POSITIONED_UPDATES**必須支援**SQL_PS_POSITIONED_DELETE**和**SQL_PS_POSITIONED_UPDATE。**

此外,如果請求悲觀鎖定,將調用`SQLSetPos`irow 1、fRefresh FALSE 和 fLock **SQL_LCK_EXCLUSIVE。**

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
