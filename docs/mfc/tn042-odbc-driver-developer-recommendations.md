---
title: "TN042: ODBC 驅動程式開發人員建議 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.odbc
dev_langs: C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad6361266ebf2f09b8f34d150de835b25c55720b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042：ODBC 驅動程式開發人員建議
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示會說明 ODBC 驅動程式撰寫人員的指導方針。 本文將概述一般需求與 ODBC 功能可讓 MFC 資料庫類別，以及各種預期的語意詳細資料的假設。 所需的驅動程式的功能來支援三個`CRecordset`開啟模式 (**forwardOnly**，**快照**和**動態**) 所述。  
  
## <a name="odbcs-cursor-library"></a>ODBC 的資料指標程式庫  
 MFC 資料庫類別呈現給使用者，在許多情況下超出大多數的層級 1 ODBC 驅動程式所提供的功能的功能。 幸運的是，ODBC 的資料指標程式庫自行驅動程式時，資料庫類別之間分層，將會自動提供許多此額外的功能。  
  
 例如，大多數 1.0 驅動程式不支援向後捲動。 資料指標程式庫可以偵測此項目，並會快取驅動程式中的資料列並將其呈現 FETCH_PREV 呼叫中要求**SQLExtendedFetch**。  
  
 資料指標程式庫相依性的另一個重要的範例是定位的更新。 大多數 1.0 驅動程式也不需要定位的更新，但資料指標程式庫將會產生用來識別目標資料列，根據其目前的快取的資料值或快取的時間戳記值的資料來源上的 update 陳述式。  
  
 類別庫會永遠不會使用多個資料列集。 因此，少數**SQLSetPos**陳述式一律會套用到資料列 1 資料列集。  
  
## <a name="cdatabases"></a>CDatabases  
 每個`CDatabase`配置單一**HDBC**。 (如果`CDatabase`的`ExecuteSQL`函式使用時， **HSTMT**暫時配置。)因此，如果多個`CDatabase`的需要，多個**HDBC**每 s **HENV**必須支援。  
  
 資料庫類別要求資料指標程式庫。 這會反映在**SQLSetConnections**呼叫**SQL_ODBC_CURSORS**， **SQL_CUR_USE_ODBC**。  
  
 **SQLDriverConnect**， **SQL_DRIVER_COMPLETE**正由`CDatabase::Open`來建立資料來源的連接。  
  
 此驅動程式必須支援**SQLGetInfo SQL_ODBC_API_CONFORMANCE** >= **SQL_OAC_LEVEL1**， **SQLGetInfo SQL_ODBC_SQL_CONFORMANCE**  >= **SQL_OSC_MINIMUM**。  
  
 為了讓交易支援`CDatabase`和其相依的資料錄集， **SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR**和**SQL_CURSOR_ROLLBACK_BEHAVIOR**必須**SQL_CR_PRESERVE**。 否則，嘗試執行交易控制都會被忽略。  
  
 **SQLGetInfo SQL_DATA_SOURCE_READ_ONLY**必須支援。 如果它傳回"Y"，將資料來源上不執行任何 update 作業。  
  
 如果`CDatabase`開啟 ReadOnly，設定讀取的資料來源只會嘗試建立與**SQLSetConnectOption SQL_ACCESS_MODE**， **SQL_MODE_READ_ONLY**。  
  
 如果識別項會需要用引號括住，這項資訊應該會傳回從驅動程式搭配**SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR**呼叫。  
  
 以進行偵錯， **SQLGetInfo SQL_DBMS_VER**和**SQL_DBMS_NAME**從驅動程式擷取。  
  
 **SQLSetStmtOption SQL_QUERY_TIMEOUT**和**SQL_ASYNC_ENABLE**上無法呼叫`CDatabase`的**HDBC**。  
  
 **SQLError**可能使用任何或所有引數 NULL 呼叫。  
  
 當然， **SQLAllocEnv**， **SQLAllocConnect**， **SQLDisconnect**和**SQLFreeConnect**必須支援。  
  
## <a name="executesql"></a>ExecuteSQL  
 除了配置及釋放暫存**HSTMT**，`ExecuteSQL`呼叫**SQLExecDirect**， **SQLFetch**， **SQLNumResultCol**和`SQLMoreResults`。 **SQLCancel**上無法呼叫**HSTMT**。  
  
## <a name="getdatabasename"></a>GetDatabaseName  
 **SQLGetInfo SQL_DATABASE_NAME**將呼叫。  
  
## <a name="begintrans-committrans-rollback"></a>BeginTrans，CommitTrans，復原  
 **SQLSetConnectOption SQL_AUTOCOMMIT**和**SQLTransact SQL_COMMIT**， **SQL_ROLLBACK**和**SQL_AUTOCOMMIT**如果將會呼叫交易發出要求。  
  
## <a name="crecordsets"></a>CRecordsets  
 **SQLAllocStmt**， **SQLPrepare**， **SQLExecute** (如**開啟**和**Requery**)， **SQLExecDirect** （適用於更新作業）， **SQLFreeStmt**必須支援。 **SQLNumResultCols**和**SQLDescribeCol**會對呼叫的結果集的不同時間。  
  
 **SQLSetParam**廣泛用於參數將資料繫結和**DATA_AT_EXEC**功能。  
  
 **SQLBindCol**註冊大量使用輸出資料行的資料儲存位置使用 ODBC。  
  
 兩個**SQLGetData**呼叫用來擷取**SQL_LONG_VARCHAR**和**SQL_LONG_VARBINARY**資料。 第一次呼叫會嘗試尋找資料行值的總長度，藉由呼叫**SQLGetData** cbMaxValue 為 0，但有效 pcbValue。 如果 pcbValue 持有**SQL_NO_TOTAL**，擲回例外狀況。 否則，`HGLOBAL`配置時，和另一個**SQLGetData**呼叫以擷取整個結果。  
  
## <a name="updating"></a>Updating  
 如果封閉式鎖定要求， **SQLGetInfo SQL_LOCK_TYPES**要查詢。 如果**SQL_LCK_EXCLUSIVE**是不受支援，將會擲回例外狀況。  
  
 嘗試更新`CRecordset`(**快照**或**動態**) 會導致第二個**HSTMT**配置。 不支援的驅動程式的第二個**HSTMT**，資料指標程式庫會模擬此功能。 不幸的是，這可能有時表示目前的查詢強制在第一個**HSTMT**完成之前先處理第二個**HSTMT**的要求。  
  
 **SQLFreeStmt SQL_CLOSE**和**SQL_RESET_PARAMS**和**SQLGetCursorName**將更新作業期間呼叫。  
  
 如果沒有**CLongBinarys**中**outputColumns**，ODBC 的**DATA_AT_EXEC**必須支援的功能。 這包括傳回**SQL_NEED_DATA**從**SQLExecDirect**， **SQLParamData**和**SQLPutData**。  
  
 **SQLRowCount**呼叫之後執行，以確認只有 1 個記錄已由更新**SQLExecDirect**。  
  
## <a name="forwardonly-cursors"></a>ForwardOnly 資料指標  
 只有**SQLFetch**需要**移動**作業。 請注意， **forwardOnly**資料指標不支援更新。  
  
## <a name="snapshot-cursors"></a>快照集資料指標  
 快照集功能需要**SQLExtendedFetch**支援。 如先前所述，驅動程式不支援時，會偵測到 ODBC 資料指標程式庫**SQLExtendedFetch**，並提供必要的支援本身。  
  
 **SQLGetInfo**， **SQL_SCROLL_OPTIONS**必須支援**SQL_SO_STATIC**。  
  
## <a name="dynaset-cursors"></a>動態資料指標  
 以下是開啟動態集所需的最小支援：  
  
 **SQLGetInfo**， **SQL_ODBC_VER**必須傳回 >"01"。  
  
 **SQLGetInfo**， **SQL_SCROLL_OPTIONS**必須支援**SQL_SO_KEYSET_DRIVEN**。  
  
 **SQLGetInfo**， **SQL_ROW_UPDATES**必須傳回"Y"。  
  
 **SQLGetInfo**， **SQL_POSITIONED_UPDATES**必須支援**SQL_PS_POSITIONED_DELETE**和**SQL_PS_POSITIONED_UPDATE**。  
  
 此外，如果要求封閉式鎖定時，呼叫**SQLSetPos** irow 1、 fRefresh FALSE 與 fLock **SQL_LCK_EXCLUSIVE**不會進行。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

