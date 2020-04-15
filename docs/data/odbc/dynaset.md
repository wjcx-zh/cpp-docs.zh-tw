---
title: 動態集
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371832"
---
# <a name="dynaset"></a>動態集

這個主題介紹動態集並討論其[可用性](#_core_availability_of_dynasets)。

> [!NOTE]
> 本主題適用於 MFC ODBC 類,包括[CRecordset。](../../mfc/reference/crecordset-class.md) 有關 DAO 類別的動態的資訊,請參考[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 使用 DAO,您可以打開動態集類型的記錄集。

動態集是具有動態屬性的記錄集。 在其生存期內,動態集模式下的記錄集物件(通常稱為動態集)以以下方式與數據源保持同步。 在多使用者環境中,其他使用者可能會編輯或刪除動態集中的記錄,或將記錄添加到動態集所代表的表中。 應用程式添加到的記錄集中添加或刪除的記錄將反映在動態集中。 其他使用者添加到表的記錄不會反映在動態集中,直到您通過調用其`Requery`成員函數重建動態集。 當其他使用者刪除記錄時,MFC 代碼將跳過記錄集中的刪除。 捲動到受影響的記錄後,其他使用者對現有記錄的編輯更改將立即反映在動態集中。

同樣,對動態集中記錄進行的編輯將反映在其他使用者正在使用的動態集中。 您添加的記錄不會反映在其他使用者的動態集中,直到他們重新查詢其動態集。 您刪除的記錄在其他使用者的記錄集中標記為" 已刪除。 如果有多個連接到同一數據庫(`CDatabase`多個物件),則與這些連接關聯的記錄集具有與其他使用者的記錄集相同的狀態。

當數據必須是動態的時,Dynaset 最有價值,例如航空公司預訂系統中的數據。

> [!NOTE]
> 要使用動態集,必須為資料源提供支援動態集的 ODBC 驅動程式,並且不得載入 ODBC 游標庫。 有關詳細資訊,請參閱[動態集的可用性](#_core_availability_of_dynasets)。

要指定記錄集是動態集,請作為第一個`CRecordset::dynaset`參數傳遞給記錄集`Open`對象的成員函數。

> [!NOTE]
> 對於可更新的發電機組,您的 ODBC 驅動程式必須支援定位更新語`::SQLSetPos`句或 ODBC API 功能。 如果兩者都支援,MFC`::SQLSetPos`用於提高效率。

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dynasets 可用性

如果滿足以下要求,MFC 資料庫類支援動態集:

- ODBC 游標庫 DLL 不得用於此資料來源。

   如果使用游標庫,它將遮罩基礎ODBC驅動程式的某些功能,這些功能對於動態設置支援是必需的。 如果要使用動態集(並且 ODBC 驅動程式具有動態集所需的功能(如本節其餘部分所述),可能會導致 MFC 在創建`CDatabase`物件時不載入游標庫。 有關詳細資訊,請參閱[ODBC](../../data/odbc/odbc-basics.md)`CDatabase`和類的[OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[Open](../../mfc/reference/cdatabase-class.md#open)成員函數。

   在 ODBC 術語中,動態集和快照稱為游標。 游標是用於跟蹤其在記錄集中的位置的機制。

- 數據源的 ODBC 驅動程式必須支援鍵集驅動的遊標。

   Keyset 驅動的游標通過獲取和儲存一組金鑰來管理表中的數據。 當使用者滾動到特定記錄時,這些鍵用於從表中獲取當前數據。 要確定驅動程式是否提供此支援,請使用`::SQLGetInfo`*SQL_SCROLL_OPTIONS*參數呼叫ODBC API函數。

   如果嘗試在沒有金鑰集支援的情況下開啟動態集,則AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED取得具有返回代碼`CDBException`值的 。

- 數據源的 ODBC 驅動程式必須支援擴展提取。

   擴展提取是向後滾動和向前滾動 SQL 查詢的結果記錄的能力。 要確定驅動程式是否支援此功能,請使用*SQL_API_SQLEXTENDEDFETCH*SQL_API_SQLEXTENDEDFETCH`::SQLGetFunctions`參數調用 ODBC API 函數。

如果需要可更新的動態集(或快照),ODBC 驅動程式還必須`::SQLSetPos`支援 ODBC API 功能或定位更新。 該`::SQLSetPos`函數允許 MFC 在不發送 SQL 語句的情況下更新數據源。 如果此支援可用,MFC 會將其用於使用 SQL 進行更新。 要確定驅動程式是否支援`::SQLSetPos`,`::SQLGetInfo`請使用*SQL_POS_OPERATIONS*參數呼叫。

定位更新使用 SQL\<語法 (>)**識別**數據來源表中的特定行。 要確定驅動程式是否支援定位更新,請使用`::SQLGetInfo`*SQL_POSITIONED_STATEMENTS*參數進行調用。

通常,MFC 動態集(但不只轉發記錄集)需要具有 2 級 API 一致性的 ODBC 驅動程式。 如果資料源的驅動程式符合 1 級 API 集,您仍可以使用可更新和唯讀快照和僅轉發記錄集,但不能使用動態集。 但是,如果級別 1 驅動程式支援擴展提取和鍵集驅動的遊標,則可以支援動態集。 有關 ODBC 符合性層級的詳細資訊,請參閱[ODBC](../../data/odbc/odbc-basics.md)。

> [!NOTE]
> 如果要同時使用快照和動態集,則必須將它們基於兩個不同的`CDatabase`物件(兩個不同的連接)。

與使用 ODBC 遊標庫維護的中間存儲的快照不同,動態集在滾動到數據源時直接從數據源獲取記錄。 這樣,最初由動態集選擇的記錄與數據源保持同步。

如需此版本 Visual C++ 隨附之 ODBC 驅動程式的清單，以及取得其他驅動程式的相關資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
