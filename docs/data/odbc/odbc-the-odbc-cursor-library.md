---
title: ODBC：ODBC 資料指標程式庫
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367185"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 資料指標程式庫

本主題介紹 ODBC 游標庫,並說明如何使用它。 如需詳細資訊，請參閱

- [游標庫與 1 級 ODBC 驅動程式](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [定位更新與時間戳欄](#_core_positioned_updates_and_timestamp_columns)

- [使用游標庫](#_core_using_the_cursor_library)

ODBC 游標庫是一個動態連結庫 (DLL),位於 ODBC 驅動程式管理器和驅動程式之間。 在 ODBC 術語中,驅動程式維護一個游標,以追蹤其在記錄集中的位置。 游標記您已捲軸到的記錄集中的位置 - 目前的紀錄。

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>游標庫與 1 級 ODBC 驅動程式

ODBC 游標庫為 1 層式驅動程式提供以下新功能:

- 向前和向後滾動。 級別 2 驅動程式不需要游標庫,因為它們已經是可滾動的。

- 支援快照。 游標庫管理包含快照記錄的緩衝區。 此緩衝區反映程式對記錄的刪除和編輯,而不是其他使用者的添加、刪除或編輯。 因此,快照僅與游標庫的緩衝區一樣最新。 在調用`Requery`之前,緩衝區也不會反映您自己的添加。 動態集不使用游標庫。

游標庫為您提供快照(靜態游標),即使驅動程式通常不支援快照也是如此。 如果驅動程式已支援靜態游標,則無需載入游標庫來獲取快照支援。 如果使用遊標庫,則只能使用快照和僅轉發記錄集。 如果驅動程式支援動態集(KEYSET_DRIVEN游標),並且想要使用它們,則不得使用游標庫。 如果要同時使用快照和動態集,則必須將它們基於兩個不同的`CDatabase`物件(兩個不同的連接),除非您的驅動程式支援這兩個物件。

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>定位更新與時間戳欄

> [!NOTE]
> ODBC 資料來源可透過 MFC ODBC 類別(如本主題所述)或透過 MFC 資料存取物件 (DAO) 類別存取。

> [!NOTE]
> 如果您的 ODBC`SQLSetPos`驅動程式 支援 MFC 使用(如果可用),則本主題不適用於您。

大多數1級驅動程式不支援定位更新。 此類驅動程式依賴於游標庫來類比 2 級驅動程式在這方面的功能。 游標庫通過在不變的欄位上執行搜索更新來類比定位更新支援。

在某些情況下,記錄集可能包含時間戳列作為這些不變欄位之一。 使用包含時間戳列的表的 MFC 記錄集會產生兩個問題。

第一個問題涉及具有時間戳列的表上的可更新快照。 如果快照繫結到的表格包含時間戳列,則應在呼`Requery``Edit`叫`Update`與 後呼叫 。 如果沒有,可能無法再次編輯同一記錄。 調用`Edit``Update`然後 調用 時,記錄將寫入數據源,並更新時間戳列。 如果不調用`Requery`,快照中記錄的時間戳值不再與數據源上的相應時間戳匹配。 當您嘗試再次更新記錄時,數據源可能會由於不匹配而禁止更新。

第二個問題涉及類[CTime](../../atl-mfc-shared/reference/ctime-class.md)`RFX_Date`在與 函數一起使用時限制將時間和日期資訊傳輸到表或從表傳輸資訊。 在數據傳輸`CTime`過程中,處理物件會以額外的中間處理的形式施加一些開銷。 對於某些應用程式,`CTime`物件的日期範圍可能也太有限。 函數的`RFX_Date`新版本採用ODBC *TIMESTAMP_STRUCT*參數而不是`CTime`物件。 有關詳細資訊,請參閱`RFX_Date` *MFC 參考*中的[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>使用游標庫

當您透過調用[CDatabase:::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::打開](../../mfc/reference/cdatabase-class.md#open)連接到資料來源時,可以指定是否對資料來源使用游標庫。 如果要在該資料來源上建立快照`CDatabase::useCursorLib`,請`dwOptions`在 參數中指定`OpenEx`選項, 或為*bUseCursorLib*參數指定`Open`TRUE(預設值為 TRUE)。 如果您的 ODBC 驅動程式支援動態集,並且要在資料源上打開動態集,請不要使用遊標庫(它遮罩了動態集所需的某些驅動程式功能)。 在這種情況下,不要在`CDatabase::useCursorLib``OpenEx`中指定或指定 FALSE 中的*bUseCursorLib*`Open`bUseCursorLib 參數。

## <a name="see-also"></a>另請參閱

[ODBC 基礎知識](../../data/odbc/odbc-basics.md)
