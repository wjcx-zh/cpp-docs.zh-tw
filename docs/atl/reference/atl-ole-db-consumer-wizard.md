---
title: ATL OLE DB 消費者精靈
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 7195d712474765258ac0319539697b3517cb91b3
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552232"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 消費者精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="<=vs-2017"

此精靈會設定 OLE DB 消費者類別，其中含有透過指定的 OLE DB 提供者存取指定資料來源所需的資料繫結。

> [!NOTE]
> 此精靈要求您先在 `Class`和 **.h 檔案**欄位中輸入名稱，然後按一下 [資料來源]  按鈕來選取資料來源。

## <a name="uielement-list"></a>UIElement 清單

- **資料來源**

   [資料來源]  按鈕可讓您使用指定的 OLE DB 提供者來設定指定的資料來源。 當您按一下此按鈕時，[資料連結屬性]  對話方塊隨即出現。 如需有關建置連接字串和 [資料連結屬性]  對話方塊的詳細資訊，請參閱 Windows SDK 文件中的[資料連結 API 概觀](/previous-versions/windows/desktop/ms718102(v=vs.85))。

   下列其他資訊將說明 [資料連結屬性]  對話方塊中的索引標籤。

   - [提供者]  索引標籤

      選取適當的提供者來管理資料來源的連線。 提供者的類型通常取決於您所連線的資料庫類型。 按一下 [下一步]  按鈕或 [連線]  索引標籤。

   - [連線]  索引標籤

      此索引標籤的內容取決於您選取的提供者。 雖然有許多類型的提供者，但本節將涵蓋下列這兩個最常見資料的連線：SQL 和 ODBC 資料。 其他的則為此處所述欄位上的類似變體。

      針對 SQL 資料：

      1. **選取或輸入伺服器名稱：** 按一下下拉式清單功能表，以顯示網路上所有已註冊的資料伺服器，然後選取其中一部。

      1. **輸入要登入到伺服器的資訊：** 輸入使用者名稱和密碼以登入資料伺服器。

         > [!NOTE]
         > 有個關於 [資料連結屬性] 對話方塊中「允許儲存密碼」功能的安全性問題。 在 [輸入資訊以登入伺服器] 中，有兩個選項按鈕：
         >
         > - **使用 Windows NT 整合安全性**
         > - **使用特定的使用者名稱和密碼**
         >
         > 如果您選取 [使用特定的使用者名稱和密碼]  ，則可選擇儲存密碼 (使用「允許儲存密碼」的核取方塊)；不過，這個選項不安全。 建議您選取 [使用 Windows NT 整合安全性]  ；這個選項很安全，因為它會將密碼加密。
         > 可能有一些您想要選取 [允許儲存密碼] 的情況。 例如，如果您要釋出含有私人資料庫解決方案的程式庫，則您不應直接存取該資料庫，而是改用中介層應用程式來驗證使用者 (透過您選擇的驗證配置)，接著限制使用者可用資料的排序。

      1. **選取伺服器上的資料庫：** 按一下下拉式清單功能表，以顯示資料伺服器上所有已註冊的資料庫，然後選取其中一個。

         \-或-

         **附加資料庫檔案做為資料庫名稱：** 指定要用來做為資料庫的檔案；輸入明確的路徑名稱。

      針對 ODBC 資料：

      1. **指定資料來源：** 您可以使用資料來源名稱或連接字串。

         **使用資料來源名稱：** 此下拉式清單會顯示已在您的機器中註冊的資料來源。 您可以事先使用 ODBC 資料來源管理員來設定資料來源

         \-或-

         **使用連接字串：** 輸入您已經取得的連接字串，或按一下 [建置]  按鈕；[選取資料來源]  對話方塊隨即出現。 選取檔案或機器資料來源，然後按一下 [確定]  。

         > [!NOTE]
         > 您可以在 [伺服器總管]  中檢視現有連線的屬性來取得連接字串，或者，您可以在 [伺服器總管]  中按兩下 [新增連線]  來建立連線。

      1. **輸入要登入到伺服器的資訊：** 輸入使用者名稱和密碼以登入資料伺服器。

      1. 輸入要使用的初始目錄。

      1. 按一下 [測試連線]  ；如果測試成功，按一下 [確定]  。 如果沒有，請檢查您的登入資訊、嘗試另一個資料庫或嘗試另一部資料伺服器。

   - [進階]  索引標籤

      **網路設定：** 指定**模擬等級** (模擬用戶端時，允許伺服器使用的模擬等級；直接對應至 RPC 模擬等級) 和**保護等級** (在用戶端與伺服器之間傳送的資料保護等級；直接對應到 RPC 保護等級)。

      **其他**：在 [連接的逾時值]  中，指定逾時發生前所允許的閒置時間秒數。 在 [存取權限]  中，指定資料連線的存取權限。

      如需進階初始化屬性的詳細資訊，請參閱每個特定 OLE DB 提供者所提供的文件。

   - [全部]  索引標籤

      此索引標籤會顯示您已指定之資料來源與連線的初始化屬性摘要。 您可以編輯這些值。

      按一下 [確定]  以完成。 [選取資料庫物件]  對話方塊隨即出現。 從這個對話方塊中，選取消費者將使用的資料表、檢視或預存程序。

- **類別**

   選取資料來源之後，根據您所選取的資料表或預存程序，使用預設類別名稱填入此方塊 (請參閱下方的**選取資料來源**)。 您可以編輯類別名稱。

- **.h 檔案**

   選取資料來源之後，根據您所選取的資料表或預存程序，使用預設標頭類別名稱填入此方塊 (請參閱下方的**選取資料來源**)。 您可以編輯標頭檔的名稱或選取現有的標頭檔。

- **使用屬性**

   這個選項會指定精靈是否將使用屬性或範本宣告來建立消費者類別。 當您選取此選項時，精靈會使用屬性而非範本宣告 (這是預設選項)。 當您取消選取此選項時，精靈會使用範本宣告而非屬性。

   - 如果您針對消費者**型別**選取 [資料表]  ，精靈就會使用 `db_source` 和 `db_table` 屬性來建立資料表和資料表存取子類別宣告，並使用 `db_column` 來建立資料行對應。 例如，它會建立此對應：

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      而不使用 `CTable` 範本類別來宣告資料表和資料表存取子類別，以及 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 巨集來建立資料行對應，如此範例所示：

        ```cpp
        // Table accessor class
            class COrdersAccessor; // Table class
            class COrders : public CTable<CAccessor<COrdersAccessor>>;
        // ...
        // Column map
            BEGIN_COLUMN_MAP(COrderDetailsAccessor)
                COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
                COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
                // ...
            END_COLUMN_MAP()
        ```

   - 如果您針對消費者**型別**選取 [命令]  ，精靈會使用 `db_source` 和 `db_command` 屬性，並使用 `db_column` 來建立資料行對應。 例如，它會建立此對應：

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      而不使用命令類別 .h 檔案中的命令和命令存取子類別宣告，例如：

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      如需詳細資訊，請參閱[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)。

- **Type**

   選取這些選項按鈕其中一個，以指定是否將從 `CTable` 或 `CCommand` (預設值) 衍生消費者類別。

   - **資料表**

      如果您想要使用 `CTable` 或 `db_table` 來建立資料表和資料表存取子類別宣告，請選取此選項。

   - **命令**

      如果您想要使用 `CCommand` 或 `db_command` 來建立命令和命令存取子類別宣告，請選取此選項。 此為預設選取項目。

- **支援**

   選取核取方塊以指定消費者中支援的更新類型 (預設值為無)。 下列各項將設定 [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85))，並在屬性設定對應中針對 [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) 設定適當的項目。

   - **變更**

      指定消費者支援更新資料列集中的資料列資料。

   - **插入**

      指定消費者支援將資料列插入至資料列集。

   - **刪除**

      指定消費者支援從資料列集刪除資料列。

::: moniker-end

## <a name="see-also"></a>另請參閱

[ATL OLE DB 消費者](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[連接字串和資料連結 (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
