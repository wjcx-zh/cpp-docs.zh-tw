---
title: 建立簡單消費者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 120829b08ab65c10cca7ab922fc4f9be732ccc53
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860806"
---
# <a name="creating-a-simple-consumer"></a>建立簡單消費者

使用 ATL 專案精靈] 和 [ATL OLE DB 消費者精靈產生的 OLE DB 範本取用者。

### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>若要建立的 OLE DB 取用者的主控台應用程式

1. 按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。

   [ **新增專案** ] 對話方塊隨即出現。

1. 在 專案類型 窗格中，按一下**Visual c + + 專案**資料夾，然後再按一下**Win32 專案**範本 窗格中的圖示。 在 **名稱**方塊中，輸入您的專案的名稱，例如**MyCons**。

1. 按一下 [確定 **Deploying Office Solutions**]。

   Win32 專案精靈 隨即出現。

1. 在 **應用程式設定**頁面上，選取**主控台應用程式**，然後選取**新增 ATL 支援**。

1. 按一下 **完成**關閉精靈並產生專案。

接下來，使用 [ATL OLE DB 消費者精靈] 來新增 OLE DB 取用者物件。

#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>若要使用 [ATL OLE DB 消費者精靈] 建立消費者

1. 在 [類別檢視] 中以滑鼠右鍵按一下 `MyCons` 專案。

1. 在捷徑功能表，按一下 **新增**，然後按一下**加入類別**。

   **加入類別** 對話方塊隨即出現。

1. 在 [分類] 窗格中，按一下**Visual c + +**，按一下**ATL OLE DB 消費者**圖示，在範本窗格中，然後按一下**開啟**。

   ATL OLE DB 消費者精靈 隨即出現。

1. 按一下 [**資料來源**] 按鈕。

   **資料連結屬性** 對話方塊隨即出現。

1. 在 **資料連結屬性**對話方塊方塊中，執行下列動作：

   - 在 **提供者**索引標籤上，指定 OLE DB 提供者。

   - 在 **連線**索引標籤上，指定伺服器上的伺服器名稱、 登入識別碼和您的資料來源和資料庫的密碼。

   > [!NOTE]
   > 安全性問題**允許儲存密碼**功能**資料連結屬性** 對話方塊。 在 **輸入登入伺服器的資訊**，有兩個選項按鈕：**使用 Windows NT 整合式安全性**並**使用特定的使用者名稱和密碼**。

   > [!NOTE]
   > 如果您選取**使用特定的使用者名稱和密碼**，您可以選擇儲存密碼 (使用**允許儲存密碼**核取方塊); 不過，此選項並不安全。 建議您選取**使用 Windows NT 整合式安全性**; 此選項會使用 Windows NT 驗證您的身分識別。

   > [!NOTE]
   > 如果您無法使用 Windows NT 整合式安全性，您就應該使用的中介層應用程式，以提示使用者輸入密碼，或將密碼儲存在一個位置，安全性機制，以便協助保護它 (而不是在原始程式碼中)。

   選取您的提供者，以及其他設定後，按一下**測試連接**確認先前的對話方塊頁面上所做的選擇。 如果**結果**方塊報告`Test connection succeeded`，按一下 **確定**建立資料連結。

   **選取資料庫物件** 對話方塊隨即出現。

1. 您可以使用樹狀結構控制項中，選取資料表、 檢視表或預存程序。 為了此程序中，選取從 Northwind 資料庫的 Products 資料表。

1. 按一下 [確定 **Deploying Office Solutions**]。 這會讓您回到 ATL OLE DB 消費者精靈。

1. 在精靈完成的名稱`Class`並 **.h 檔案**根據名稱的資料表、 檢視或預存程序，您已選取。 如果您想要您可以編輯這些名稱。

1. 清除**屬性化**核取方塊，使精靈可讓您建立取用者程式碼使用[OLE DB 範本類別](../../data/oledb/ole-db-consumer-templates-reference.md)而非預設[OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)。

1. 底下**型別**，選取**命令**。

   此精靈會建立[CCommand](../../data/oledb/ccommand-class.md)-根據取用者，如果您選取**命令**或有[CTable](../../data/oledb/ctable-class.md)-根據取用者，如果您選取**資料表**。 選取的物件，來命名之資料表或命令的類別，但您可以編輯名稱。

1. 底下**支援**，保留**變更**，**插入**，以及**刪除**清除的方塊。

   選取 **變更**，**插入**，並**刪除**支援變更、 插入及刪除資料列集中的記錄，如有必要的核取方塊。 如需有關將資料寫入至資料存放區，請參閱 <<c0> [ 更新資料列集](../../data/oledb/updating-rowsets.md)。

1. 按一下 **完成**建立取用者。

在精靈產生的命令類別和使用者記錄類別，如中所示[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)。 命令類別會具有您在中輸入的名稱`Class`方塊中的精靈 (在此情況下， `CProducts`)，而使用者記錄類別將表單的名稱 」*ClassName*存取子 」 (在此情況下， `CProductsAccessor`)。

> [!NOTE]
> 精靈會將下面這一行放 Products.h:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> 這一行可防止消費者應用程式無法編譯，並提醒您檢查您的連接字串硬式編碼的密碼。 檢查您的連接字串之後, 您可以移除這行程式碼。

## <a name="see-also"></a>另請參閱

[使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
