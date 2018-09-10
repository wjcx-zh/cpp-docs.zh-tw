---
title: ATL OLE DB 消費者精靈 |Microsoft Docs
ms.custom: ''
ms.date: 08/31/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec6c778c46998ba8e324fcf97c209598cc2f99dd
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315365"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 消費者精靈

這個精靈設定的 OLE DB 取用者類別與資料繫結到指定的 OLE DB 提供者存取指定的資料來源所需的。

> [!NOTE]
> 此精靈會要求您按**資料來源**按鈕來選取資料來源中的名稱之前，請先`Class`並 **.h 檔案**欄位。

## <a name="uielement-list"></a>UIElement 清單

- **資料來源**

   **資料來源**按鈕可讓您設定使用指定的 OLE DB 提供者的指定的資料來源。 當您按一下此按鈕時，**資料連結屬性** 對話方塊隨即出現。 如需有關建置連接字串和**資料連結屬性** 對話方塊中，請參閱[資料連結 API 概觀](/previous-versions/windows/desktop/ms718102\(v=vs.85\))Windows SDK 文件。

   下列的其他資訊將說明中的索引標籤**資料連結屬性** 對話方塊。

   - **提供者** 索引標籤

      選取適當的提供者來管理資料來源的連接。 提供者的類型通常取決於您所連接的資料庫的類型。 按一下 [**下一步**按鈕，或按一下**連線**] 索引標籤。

   - **連接** 索引標籤

      此索引標籤的內容取決於您選取的提供者。 雖然有許多類型的提供者，但此章節將涵蓋這兩個連線最常見： SQL 和 ODBC 的資料。 有些則是類似的變體，在此處所述的欄位。

      對於 SQL 資料：

      1. **選取或輸入伺服器名稱：** 按一下下拉式清單中要顯示的功能表已註冊之資料的所有伺服器在網路上，然後選取其中一個。

      2. **輸入要登入伺服器的資訊：** 輸入使用者名稱和密碼來登入的資料伺服器。

         > [!NOTE]
         > 沒有與 [資料連結屬性] 對話方塊中的 「 允許儲存密碼 」 功能的安全性問題。 在 輸入資訊以登入伺服器 」，有兩個選項按鈕：
         >
         > - **使用 Windows NT 整合式安全性**
         > - **使用特定的使用者名稱和密碼**
         >
         > 如果您選取**使用特定的使用者名稱和密碼**，您可以選擇儲存密碼 （使用如 「 允許儲存密碼 」 的核取方塊）; 不過，這是不安全的選項。 建議您選取**使用 Windows NT 整合式安全性**; 這個選項很安全，因為它會加密密碼。
         > 可能會有一些情況，您要在其中選取 「 允許儲存密碼。 」 比方說，如果您要釋出一個私用的資料庫解決方案的程式庫，您應該直接存取資料庫，但改為使用中介層應用程式驗證使用者 （透過您選擇的驗證配置），並接著限制之資料的排序提供給使用者。

      3. **選取的伺服器上的資料庫：** 按一下下拉式清單功能表來顯示所有已註冊的資料庫伺服器上的資料，然後選取其中一個。

         \-或-

         **附加資料庫檔案做為資料庫名稱：** 指定要做為資料庫檔案，輸入明確的路徑名稱。

      對於 ODBC 資料：

      1. **指定的資料來源：** 您可以使用資料來源名稱或連接字串。

         **使用資料來源名稱：** 這個下拉式清單會顯示在您的電腦中註冊的資料來源。 您可以設定資料來源，事先使用 ODBC 資料來源管理員

         \-或-

         **使用連接字串：** 輸入您已取得，或按一下 [連接字串**建置**按鈕;**選取資料來源**] 對話方塊隨即出現。 選取檔案或機器的資料來源，然後按一下**確定**。

         > [!NOTE]
         > 您可以在 伺服器總管 中，檢視現有連接的屬性，以取得連接字串，或您可以建立連線，按兩下**加入連接**伺服器總管 中。

      2. **輸入要登入伺服器的資訊：** 輸入使用者名稱和密碼來登入的資料伺服器。

      3. 輸入要使用的初始目錄。

      4. 按一下 **測試連接**; 如果測試成功，按一下**確定**。 如果沒有，檢查您的登入資訊，請嘗試另一個資料庫，或嘗試另一部資料伺服器。

   - **進階** 索引標籤

      **網路設定：** 指定**模擬層級**（伺服器允許使用時模擬用戶端; 直接對應至 RPC 模擬層級的模擬層級） 和**保護層級**（用戶端與伺服器之間傳送的資料保護的層級直接對應至 RPC 保護層級）。

      **其他：** 中**連接的逾時值**，指定的逾時之前所允許的閒置時間的秒數。 在 **存取權限**，資料連線指定的存取權限。

       如需進階的初始化屬性的詳細資訊，請參閱每個特定的 OLE DB 提供者所提供的文件。

   - **所有** 索引標籤

      此索引標籤會顯示您所指定的連接與資料來源初始化屬性的摘要。 您可以編輯這些值。

   按一下 **確定**才能完成。 **選取資料庫物件** 對話方塊隨即出現。 從這個對話方塊中，選取資料表、 檢視或取用者會使用的預存程序。

- **類別**

   選取資料來源之後，根據資料表或您所選取的預存程序的預設類別名稱填入這個方塊 (請參閱**Zdroj dat**下方)。 您可以編輯的類別名稱。

- **.h 檔案**

   選取資料來源之後，以根據您選取的預存程序的資料表預設標頭的類別名稱填入這個方塊 (請參閱**Zdroj dat**下方)。 您可以編輯的標頭檔的名稱，或選取現有的標頭檔。

- **使用屬性**

   這個選項會指定精靈是否會建立使用屬性或宣告範本的取用者類別。 當您選取此選項時，精靈會使用屬性代替樣板宣告 （這是預設選項）。 當您取消選取此選項時，精靈會使用樣板宣告，而非屬性。

   - 如果您選取消費者**型別**的**資料表**，精靈會使用`db_source`並`db_table`屬性來建立資料表和資料表的存取子類別宣告，並使用`db_column`來建立資料行對應。 比方說，它會建立此對應：

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      而不是使用`CTable`範本類別來宣告資料表和資料表的存取子類別和 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 巨集來建立資料行對應，如此範例所示：

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

   - 如果您選取消費者**型別**的**命令**，精靈會使用`db_source`並`db_command`屬性，並使用`db_column`來建立資料行對應。 比方說，它會建立此對應：

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      而不使用的命令和命令存取子類別宣告中之命令類別的.h 檔案中，例如：

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      請參閱[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。

- **Type**

   選取其中一個這些選項按鈕，以指定是否將取用者類別衍生自`CTable`或`CCommand`（預設值）。

   - **資料表**

      如果您想要使用，請選取此選項`CTable`或`db_table`來建立資料表和資料表的存取子類別宣告。

   - **命令**

      如果您想要使用，請選取此選項`CCommand`或`db_command`建立命令和命令的存取子類別宣告。 這是預設選項。

- **支援**

   選取核取方塊，以指定的取用者 （預設值為 none） 支援的更新類型。 下列各項將會設定[DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892\(v=vs.85\))和適當的項目，如[DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676\(v=vs.85\))屬性中設定對應。

   - **變更**

      指定取用者，在資料列集支援的資料列資料的更新。

   - **插入**

      指定取用者支援插入資料列集的資料列。

   - **刪除**

      指定取用者支援的資料列集資料列的刪除。

## <a name="see-also"></a>另請參閱

[ATL OLE DB 消費者](../../atl/reference/adding-an-atl-ole-db-consumer.md)
[使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
[連接字串和資料連結 (OLE DB)](/previous-versions/windows/desktop/ms718376\(v=vs.85\))
