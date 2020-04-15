---
title: MFC ODBC 消費者精靈
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373014"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 消費者精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="<=vs-2017"

此嚮導設定 ODBC 記錄集類以及訪問指定數據源所需的數據綁定。

## <a name="uielement-list"></a>UIElement 清單

- **資料來源**

  使用**資料來源**按鈕,您可以使用指定的 ODBC 驅動程式設定指定的資料來源。 關於資料來源檔案 (DSN) 的詳細資訊,請參考 ODBC SDK[中的檔案資料來源](/sql/odbc/reference/file-data-sources)。

  選擇**資料來源**對話框有兩個選項卡:

  - **檔案資料來源**選項卡:

     「**檢視」** 方塊指定選擇要用作資料來源的檔案的目錄。 預設值為 [程式檔]公共檔\ODBC_資料源。 現有檔案資料來源 (.dsn 檔) 將顯示在主清單框中。 您可以使用[ODBC 資料來源管理員](/sql/odbc/admin/odbc-data-source-administrator)上**的檔案 DSN**選項卡提前設定數據來源,也可以使用此對話框建立新資料來源。

     要從此對話框創建新的文件數據來源,請按一下以指定 DSN 名稱;單`New`擊以指定 DSN 名稱。將顯示「**創建新資料源」** 對話框。 在 **"創建新資料源'** 對話框中,選擇適當的驅動程式並`Next`按一下 ""。按下 **「瀏覽**」並選擇用作資料來源的檔案名稱(您必須選擇"所有檔案"才能查看非 DSN 檔,如 .xls 檔);按下`Next`,然後按下 **"完成**"。 (如果選擇了非 DSN 檔,您將獲得特定於驅動程式的對話框,例如"ODBC 微軟 Excel 設定",該對話方塊會將檔案轉換為 DSN。

     > [!NOTE]
     > 您還可以使用 ODBC 資料來源管理員提前創建新的檔案數據來源。 在 **「開始」** 選單中,選擇 **「設定**」、「**控制面板**」、「**管理工具**」、「**資料來源 」(ODBC),** 然後**選擇 ODBC 資料來源管理員**。

     **DSN 名稱**框允許您為檔案數據來源指定名稱。 必須確保 DSN 名稱以適當的檔副檔名結束,例如 Excel 檔的 .xls 或 Access 檔的 .mdb。

     有關 DSN 的詳細資訊,請參閱 ODBC SDK 中[的檔案資料來源](/sql/odbc/reference/file-data-sources)。

  - **電腦資料來源**選項卡:

     此選項卡列出了系統和用戶數據來源。 使用者數據源特定於此電腦上的使用者。 系統數據源可以由此電腦上的所有使用者或系統範圍的服務使用。 請參考 ODBC SDK 中的[機器資料來源](/sql/odbc/reference/machine-data-sources)

     有關 ODBC 資料來源的詳細資訊,請參閱 ODBC SDK 中的[資料來源](/sql/odbc/reference/data-sources)。

  按一下 [確定]**** 以完成。 [選取資料庫物件]**** 對話方塊隨即出現。 在此對話框中,選擇消費者將使用的表或視圖。 請注意,在單擊專案時,可以通過按住控制鍵來選擇多個視圖和表。 按一下 [確定]**** 以完成。

- **類別**

   消費者類的名稱,默認情況下基於您選擇的檔案或計算機數據源的名稱。

- **.h 檔案**

   消費者類標頭檔的名稱,默認情況下基於您選擇的檔案或計算機數據源的名稱。

- **.cpp 檔案**

   消費者類實現檔的名稱,預設情況下基於您選擇的檔案或計算機數據源的名稱。

- **型別**

   指定記錄集是動態集(預設)還是快照。

  - **動態集**:指定記錄集是動態集。 動態集是查詢的結果,該查詢向查詢資料庫的數據提供索引視圖。 動態集僅緩存原始數據的整體索引,因此比快照提供性能提升。 索引直接指向查詢結果找到的每個記錄,並指示是否刪除了記錄。 您還可以存取查詢記錄中的更新資訊。 這是預設值。

  - **快照**:指定記錄集是快照。 快照是查詢的結果,是某個時間點對資料庫的視圖。 查詢結果找到的所有記錄都將被快取,因此您看不到對原始記錄的任何更改。

- **繫結所有欄**

   指定是否綁定所選表中的所有欄。 如果選擇此框(預設值),則所有列都綁定;如果選擇此框(預設值),則所有列都綁定。如果不選擇此框,則不會綁定任何列,並且必須在記錄集類中手動綁定它們。

::: moniker-end

## <a name="see-also"></a>另請參閱

[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
