---
title: MFC ODBC 消費者精靈
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 2e8741677031ff9b12989d75243a13550d74b608
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707377"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 消費者精靈

::: moniker range="vs-2019"

此精靈不是可在 Visual Studio 2019 及更新版本。

::: moniker-end

::: moniker range="<=vs-2017"

此精靈設定 ODBC 資料錄集類別和資料繫結存取指定的資料來源所需。

## <a name="uielement-list"></a>UIElement 清單

- **資料來源**

  **資料來源**按鈕可讓您設定指定的資料來源，使用指定的 ODBC 驅動程式。 如需有關資料來源檔案 (DSN) 的詳細資訊，請參閱[檔案資料來源](/sql/odbc/reference/file-data-sources)ODBC SDK 中。

  **選取資料來源**對話方塊有兩個索引標籤：

  - **檔案資料來源** 索引標籤：

     **查看** 方塊中指定要在其中選取要用作資料來源檔案的目錄。 預設為 \Program Files\Common Files\ODBC\Data 來源。 現有的檔案資料來源 （.dsn 檔案） 會出現在 [主要] 清單方塊中。 您可以設定註冊前階段使用的資料來源**檔案 DSN**索引標籤上[ODBC 資料來源管理員](/sql/odbc/admin/odbc-data-source-administrator)，或建立新的使用此對話方塊。

     若要建立新的檔案資料來源從這個對話方塊中，按一下`New`指定的 DSN 名稱;**建立新的資料來源** 對話方塊隨即出現。 在 **建立新的資料來源**對話方塊，選取適當的驅動程式，然後按一下`Next`; 按一下**瀏覽**，，然後選取要用作資料來源 （您必須選取 所有檔案 的檔案名稱檢視非 DSN 檔案，例如.xls 檔案）;按一下  `Next`，然後按一下**完成**。 （如果您選取的非 DSN 檔案時，您會取得驅動程式專屬對話方塊中，例如"ODBC Microsoft Excel Setup"這會將檔案轉換成資料來源名稱）。

     > [!NOTE]
     > 您也可以建立新的檔案資料來源，事先使用 ODBC 資料來源管理員。 從**開始**功能表上，選取**設定**，**控制台**，**系統管理工具**，**資料來源 (ODBC)**，然後**ODBC 資料來源管理員**。

     **DSN 名稱**方塊可讓您指定的檔案資料來源的名稱。 您必須確定 DSN 名稱結尾適當副檔名，例如 Excel 檔案的.xls 或.mdb 檔案的存取。

     如需有關名稱 （dsn） 的詳細資訊，請參閱[檔案資料來源](/sql/odbc/reference/file-data-sources)ODBC SDK 中。

  - **資料來源的機器** 索引標籤：

     此索引標籤會列出系統和使用者資料來源。 使用者資料來源專屬於此機器上的使用者。 系統資料來源可供所有使用者在這部電腦上或全系統服務。 請參閱[機器資料來源](/sql/odbc/reference/machine-data-sources)ODBC SDK 中

     如需有關 ODBC 資料來源的詳細資訊，請參閱 < [Zdroje dat](/sql/odbc/reference/data-sources) ODBC SDK 中。

  按一下 **確定**才能完成。 **選取資料庫物件** 對話方塊隨即出現。 從這個對話方塊中，選取資料表或檢視，將會使用取用者。 請注意，您可以按住 control 鍵同時按一下的項目上選取多個檢視和資料表。 按一下 **確定**才能完成。

- **類別**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **.h 檔案**

   取用者類別標頭檔名稱，依預設是根據您選取的檔案或機器資料來源的名稱。

- **.cpp 檔**

   取用者類別實作檔中，依預設是根據您選取的檔案或機器資料來源的名稱的名稱。

- **Type**

   指定資料錄集是動態 （預設值） 或快照集。

   - **動態集**:指定資料錄集是動態集。 動態集是可查詢的資料庫資料的索引檢視表查詢的結果。 動態集快取的整數索引的原始資料，並因此提供了一效能中取得快照集。 直接到每一筆記錄的索引點找到為查詢的結果，並指出是否要移除記錄。 您也會有查詢記錄中的更新資訊的存取權。 這是預設值。

   - **快照集**:指定資料錄集是快照集。 快照是查詢的結果，而且時間是在某個時間點的資料庫的檢視。 快取查詢結果所發現的所有記錄，因此您不會看到原始記錄的任何變更。

- **所有的資料行繫結**

   指定選取的資料表中的所有資料行是否會繫結。 如果您選取此方塊 （預設值） 時，會繫結所有資料行;如果您未選取此方塊，沒有資料行繫結，以及您必須將其繫結以手動方式在資料錄集類別中。

::: moniker-end

## <a name="see-also"></a>另請參閱

[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
