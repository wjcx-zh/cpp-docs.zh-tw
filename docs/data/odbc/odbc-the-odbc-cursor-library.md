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
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213092"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 資料指標程式庫

本主題描述 ODBC 資料指標程式庫，並說明其使用方式。 如需詳細資訊，請參閱

- [資料指標程式庫和層級 1 ODBC 驅動程式](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [定點更新和時間戳記資料行](#_core_positioned_updates_and_timestamp_columns)

- [使用資料指標程式庫](#_core_using_the_cursor_library)

ODBC 資料指標程式庫是位於 ODBC 驅動程式管理員和驅動程式之間的動態連結程式庫（DLL）。 在 ODBC 詞彙中，驅動程式會維護資料指標，以追蹤其在記錄集中的位置。 資料指標會將您已經滾動的記錄集中的位置，標示為目前的記錄。

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>資料指標程式庫和層級 1 ODBC 驅動程式

ODBC 資料指標程式庫提供下列新功能給第1層驅動程式：

- 向前和向後滾動。 層級2驅動程式不需要資料指標程式庫，因為它們已經是可滾動的。

- 快照集的支援。 資料指標程式庫會管理包含快照集記錄的緩衝區。 這個緩衝區會反映您的程式對記錄的刪除和編輯，但不會反映其他使用者的新增、刪除或編輯。 因此，快照集只會與資料指標程式庫的緩衝區一樣。 在您呼叫 `Requery`之前，緩衝區也不會反映您自己的新增專案。 動態集不會使用資料指標程式庫。

資料指標程式庫會提供快照集（靜態資料指標），即使您的驅動程式通常不支援它們也一樣。 如果您的驅動程式已經支援靜態資料指標，您就不需要載入資料指標程式庫來取得快照集支援。 如果您使用資料指標程式庫，則只能使用快照集和順向記錄集。 如果您的驅動程式支援動態集（KEYSET_DRIVEN 的資料指標），而您想要使用它們，則不能使用資料指標程式庫。 如果您想要同時使用快照集和動態連結，則必須將它們以兩個不同的 `CDatabase` 物件（兩個不同的連線）作為基礎，除非您的驅動程式同時支援兩者。

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>定點更新和時間戳記資料行

> [!NOTE]
>  您可以透過 MFC ODBC 類別存取 ODBC 資料來源，如本主題中所述，或透過 MFC 資料存取物件（DAO）類別。

> [!NOTE]
>  如果您的 ODBC 驅動程式支援 `SQLSetPos`（MFC 使用的話），本主題不適用。

大部分層級1的驅動程式不支援定點更新。 這類驅動程式依賴資料指標程式庫，在這方面模擬層級2驅動程式的功能。 資料指標程式庫會在不變的欄位上執行搜尋的更新，以模擬定點更新支援。

在某些情況下，記錄集可能會包含 timestamp 資料行做為其中一個不變欄位。 搭配包含時間戳記資料行的資料表使用 MFC 記錄集時，會發生兩個問題。

第一個問題涉及具有時間戳記資料行之資料表上可更新的快照集。 如果您的快照集所系結的資料表包含 timestamp 資料行，則您應該在呼叫 `Edit` 和 `Update`後呼叫 `Requery`。 如果沒有，您可能無法再次編輯相同的記錄。 當您呼叫 `Edit` 然後 `Update`時，記錄會寫入至資料來源，而且時間戳記資料行會更新。 如果您未呼叫 `Requery`，則快照中記錄的時間戳記值將不再符合資料來源上對應的時間戳記。 當您再次嘗試更新記錄時，資料來源可能會因為不相符而禁止更新。

第二個問題在與 `RFX_Date` 函式搭配使用時，會考慮類別[CTime](../../atl-mfc-shared/reference/ctime-class.md)的限制，以便將時間和日期資訊傳送至資料表或從中傳出。 處理 `CTime` 物件會在資料傳輸期間，以額外的中繼處理形式來施加一些負擔。 對於某些應用程式而言，`CTime` 物件的日期範圍可能也太過限制。 新版本的 `RFX_Date` 函數會採用 ODBC *TIMESTAMP_STRUCT*參數，而不是 `CTime` 物件。 如需詳細資訊，請參閱*MFC 參考*中的[宏和 Globals](../../mfc/reference/mfc-macros-and-globals.md)中的 `RFX_Date`。

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>使用資料指標程式庫

當您連接到資料來源時（藉由呼叫[CDatabase：： microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open) ），您可以指定是否要使用資料來源的資料指標程式庫。 如果您要在該資料來源上建立快照集，請在 `dwOptions` 參數中指定 `CDatabase::useCursorLib` 選項來 `OpenEx`，或將*bUseCursorLib*參數指定為 true 以 `Open` （預設值為 true）。 如果您的 ODBC 驅動程式支援動態集，而您想要開啟資料來源上的動態集，請不要使用資料指標程式庫（它會遮罩動態集所需的一些驅動程式功能）。 在此情況下，請勿在 `OpenEx` 中指定 `CDatabase::useCursorLib`，或在 `Open`中為*bUseCursorLib*參數指定 FALSE。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)
