---
title: 建立簡單消費者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 0b142a73f66a796f3e22bae0aeacb88dc018aea9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501867"
---
# <a name="creating-a-simple-consumer"></a>建立簡單消費者

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍能手動新增功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="<=vs-2017"

使用 [ATL 專案精靈]**** 和 [ATL OLE DB 消費者精靈]**** 產生 OLE DB 範本消費者。

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>若要建立 OLE DB 消費者的主控台應用程式

1. 在 **[檔案]** 功能表上按一下 **[新增]**，然後按一下 **[專案]**。

   [新增專案]  對話方塊隨即出現。

1. 在 [專案類型]**** 窗格中，按一下 [已安裝]**** > [Visual C++]**** > [Windows 桌面]**** 資料夾，然後按一下 [範本]**** 窗格中的 [Windows 桌面精靈]**** 圖示。 在 [名稱]**** 方塊中，輸入您專案的名稱，例如 *MyCons*。

1. 按一下 [確定]。

   [Windows 桌面專案]**** 精靈隨即出現。

1. 在 [應用程式設定]**** 頁面上，選取 [主控台應用程式]****，然後選取 [新增 ATL 的通用標頭檔]****。

1. 按一下 [確定]**** 以關閉精靈並產生專案。

接下來，使用 [ATL OLE DB 消費者精靈]**** 新增 OLE DB 消費者物件。

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>若要使用 [ATL OLE DB 消費者精靈] 建立消費者

1. 在 **方案總管**中，以滑鼠右鍵按一下 `MyCons` 專案。

1. 在捷徑功能表上，按一下 [新增]****，然後按一下 [新增項目]****。

   [加入新項目]  對話方塊隨即出現。

1. 在 [類別]**** 窗格中，按一下 [已安裝]**[Visual C++]** > **[ATL]** > ****、按一下 [範本]**** 窗格中的 [ATL OLEDB 消費者]**** 圖示，然後按一下 [新增]****。

   [ATL OLEDB 消費者精靈]**** 隨即出現。

1. 按一下 [資料來源]**** 按鈕。

   [資料連結屬性]**** 對話方塊隨即出現。

1. 在 [資料連結屬性]**** 對話方塊中，執行下列動作：

   1. 在 [提供者]**** 索引標籤上，指定 OLE DB 提供者。

   1. 在 [連線]**** 索引標籤上，指定伺服器上所需的資訊，例如資料來源和資料庫的伺服器名稱、登入識別碼，以及密碼。

      > [!NOTE]
      > [資料連結屬性]**** 對話方塊的 [允許儲存密碼]**** 功能有一個安全性問題。 在 **[輸入資訊以登入伺服器**] 中，有兩個選項按鈕： **使用 Windows NT 整合式安全性** ，並 **使用特定的使用者名稱和密碼**。

      > [!NOTE]
      > 如果您選取 [使用特定的使用者名稱和密碼]****，則可選擇儲存密碼 (使用 [允許儲存密碼]**** 核取方塊)；不過，這個選項不安全。 建議您選取 [使用 Windows NT 整合安全性]****；這個選項會使用 Windows NT 驗證您的身分識別。

      > [!NOTE]
      > 如果您無法使用 Windows NT 整合安全性，您應該使用的中介層應用程式提示使用者輸入密碼，或使用可協助保護密碼的安全機制，將密碼儲存在一個位置 (而不是儲存在原始程式碼中)。

   1. 選取您的提供者以及其他設定後，按一下 [測試連線]**** 以確認在上一個對話方塊頁面上所做的選擇。 如果 [結果]**** 方塊報告 `Test connection succeeded`，請按一下 [確定]**** 以建立資料連結。

   [選取資料庫物件]**** 對話方塊隨即出現。

1. 使用樹狀結構控制項選取資料表、檢視或預存程序。 在此範例中，選取 `Northwind` 資料庫中的 `Products` 資料表。

1. 按一下 [確定]。 這會傳回 [ATL OLE DB 消費者精靈]****。

1. 此精靈會根據所選資料表、檢視或預存程序的名稱，填寫 `Class` 和 **.h 檔案**的名稱。 您可以視需要編輯這些名稱。

1. 清除 [使用屬性]**** 核取方塊，讓精靈使用 [OLE DB 範本類別](../../data/oledb/ole-db-consumer-templates-reference.md)而非預設的 [OLE DB 消費者屬性](../../windows/attributes/ole-db-consumer-attributes.md)建立消費者程式碼。

1. 在 [類型]**** 底下，選取 [命令]****。

   如果您選取 [命令]****，此精靈會建立 [CCommand](../../data/oledb/ccommand-class.md) 型消費者；如果您選取 [資料表]****，則會建立 [CTable](../../data/oledb/ctable-class.md) 型消費者。 資料表或命令類別是以選取的物件命名，但是您可以編輯名稱。

1. 在 [支援]**** 底下，將 [變更]****、[插入]**** 和 [刪除]**** 方塊保留為清除狀態。

   選取 [變更]****、[插入]**** 和 [刪除]**** 核取方塊可支援在資料列集中變更、插入和刪除記錄。 如需有關將資料寫入至資料存放區的詳細資訊，請參閱[更新資料列集](../../data/oledb/updating-rowsets.md)。

1. 按一下 [完成]**** 可建立消費者。

此精靈會產生一個命令類別和一個使用者記錄類別，如[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)中所示。 命令類別將擁有您在精靈的 [`Class`] 方塊中輸入的名稱 (在此例中為 `CProducts`)，而使用者記錄類別的名稱則以 "*ClassName*Accessor" 格式表示 (在此例中為 `CProductsAccessor`)。

> [!NOTE]
> 此精靈會將下列行放入 `Products.h`：

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> 這一行可防止消費者應用程式編譯，並提醒您檢查連接字串中是否有硬式編碼的密碼。 檢查連接字串之後，您可以移除這行程式碼。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用 Wizard 建立 OLE DB 的取用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
