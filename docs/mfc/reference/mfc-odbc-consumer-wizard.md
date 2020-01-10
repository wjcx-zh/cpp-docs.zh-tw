---
title: MFC ODBC 消費者精靈
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 84fdc0d180f5b1b0f2e64c3597cb474611ad3914
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177429"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 消費者精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="<=vs-2017"

此 wizard 會設定 ODBC 記錄集類別, 以及存取指定資料來源所需的資料系結。

## <a name="uielement-list"></a>UIElement 清單

- **資料來源**

  [**資料來源**] 按鈕可讓您使用指定的 ODBC 驅動程式來設定指定的資料來源。 如需資料來源檔案 (DSN) 的詳細資訊, 請參閱 ODBC SDK 中的檔案[資料來源](/sql/odbc/reference/file-data-sources)。

  [**選取資料來源**] 對話方塊有兩個索引標籤:

  - [檔案**資料來源**] 索引標籤:

     [**查詢**] 方塊會指定要在其中選取要當做資料來源使用之檔案的目錄。 預設值為 \Program Files\Common Files\ODBC\Data 來源。 現有的檔案資料來源 (.dsn 檔案) 會出現在 [主要] 清單方塊中。 您可以使用 [ [ODBC 資料來源管理員](/sql/odbc/admin/odbc-data-source-administrator)] 的 [檔案**DSN** ] 索引標籤, 在一段時間內設定資料來源, 或使用此對話方塊建立新的。

     若要從此對話方塊建立新的檔案資料來源, 請按一下`New`以指定 DSN 名稱; [**建立新的資料來源**] 對話方塊隨即出現。 在 [**建立新資料來源**] 對話方塊中, 選取適當的驅動程式`Next`, 然後按一下 **[流覽]** , 再選取要當做資料來源使用的檔案名 (您必須選取 [所有檔案] 以查看非 DSN 檔案, 例如 .xls 檔案); 按一下, 然後按一下 **[完成]。** `Next` (如果您選取非 DSN 檔案, 您會看到驅動程式特定的對話方塊, 例如「ODBC Microsoft Excel 安裝程式」, 這會將檔案轉換成 DSN。)

     > [!NOTE]
     > 您也可以事先使用 [ODBC 資料來源管理員] 來建立新的檔案資料來源。 從 [**開始**] 功能表, 依序選取 [**設定**]、[**控制台**]、[系統**管理工具**]、 **[資料來源 (odbc)** ] 和 [ **ODBC 資料來源管理員**]。

     [ **DSN 名稱**] 方塊可讓您指定檔案資料來源的名稱。 您必須確定 DSN 名稱是以適當的副檔名結束, 例如 Excel 檔案的 .xls, 或 Access 檔案的 .mdb。

     如需有關 Dsn 的詳細資訊, 請參閱 ODBC SDK 中的檔案[資料來源](/sql/odbc/reference/file-data-sources)。

  - [**電腦資料來源**] 索引標籤:

     此索引標籤會列出系統和使用者資料來源。 使用者資料來源是這部電腦上的使用者所特有。 這台電腦或全系統服務上的所有使用者都可以使用系統資料來源。 請參閱 ODBC SDK 中的[機器資料來源](/sql/odbc/reference/machine-data-sources)

     如需 ODBC 資料來源的詳細資訊, 請參閱 ODBC SDK 中的[資料來源](/sql/odbc/reference/data-sources)。

  按一下 [確定] 以完成。 [選取資料庫物件] 對話方塊隨即出現。 從這個對話方塊中, 選取取用者將使用的資料表或視圖。 請注意, 您可以在按一下專案時按住控制鍵來選取多個視圖和資料表。 按一下 [確定] 以完成。

- **類別**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **.h 檔案**

   取用者類別標頭檔的名稱 (根據預設, 在您選取的檔案或電腦資料來源的名稱上)。

- **.cpp 檔**

   取用者類別實檔案的名稱 (根據預設, 在您選取的檔案或電腦資料來源的名稱上)。

- **型別**

   指定記錄集是否為動態集 (預設值) 或快照集。

   - **動態集**:指定記錄集是動態集。 動態集是查詢的結果, 可將索引化視圖提供給查詢的資料庫資料。 動態集只會快取原始資料的整數索引, 藉此提供快照集的效能提升。 索引會直接指向查詢結果所找到的每個記錄, 並指出是否已移除記錄。 您也可以存取所查詢記錄中的已更新資訊。 這是預設值。

   - **快照**集:指定記錄集是快照集。 快照集是查詢的結果, 而且是資料庫在某個時間點的視圖。 系統會快取在查詢結果中找到的所有記錄, 因此您看不到原始記錄的任何變更。

- **系結所有資料行**

   指定所選取資料表中的所有資料行是否都已系結。 如果您選取此方塊 (預設值), 則會系結所有資料行;如果您未選取此方塊, 則不會系結任何資料行, 而且您必須在記錄集類別中手動系結它們。

::: moniker-end

## <a name="see-also"></a>另請參閱

[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
