---
title: MFC ActiveX 控制項精靈、控制項名稱
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077510"
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項名稱

指定控制項類別和屬性頁類別的名稱、類型名稱，以及控制項的類型識別碼。 除了**簡短名稱**以外，所有其他欄位都可以單獨編輯。 如果您變更 [**簡短名稱**] 的文字，此變更會反映在此頁面中所有其他欄位的名稱。 此命名行為旨在讓您開發控制項時，能夠輕鬆地識別所有名稱。

- **簡短名稱**

   提供控制項的縮寫名稱。 根據預設，此名稱是以您在 [**新增專案**] 對話方塊中提供的專案名稱為基礎。 您所提供的名稱會決定類別名稱、類型名稱和類型識別碼，除非您個別變更這些欄位。

- **控制項類別名稱**

   根據預設，控制項類別的名稱是以簡短名稱為基礎，並以 `C` 做為前置詞，`Ctrl` 做為尾碼。 例如，如果 `Price`控制項的簡短名稱，則會 `CPriceCtrl`控制項類別名稱。

- **控制 .h 檔案**

   根據預設，標頭檔的名稱是以簡短名稱為依據，加上 `Ctrl` 做為尾碼，`.h` 做為副檔名。 例如，如果您的控制項的簡短名稱是 `Price`，標頭檔名稱就會是 `PriceCtrl.h`。 此欄位中的名稱應符合控制項類別名稱。

- **控制 .cpp 檔案**

   根據預設，標頭檔的名稱是以簡短名稱為依據，加上 `Ctrl` 做為尾碼，`.cpp` 做為副檔名。 例如，如果您的控制項的簡短名稱是 `Price`，標頭檔名稱就會是 `PriceCtrl.cpp`。 此欄位中的名稱應符合標頭名稱。

- **控制項類型名稱**

   根據預設，控制項類型的名稱是以簡短名稱為基礎，後面接著 `Control`。 例如，如果 `Price`控制項的簡短名稱，則會 `Price Control`控制項類別類型名稱。 如果您變更此欄位中的值，請確定名稱指出繼承。

- **控制項類型識別碼**

   設定控制項類別的控制項類型 ID。 當控制項新增至專案時，控制項會將此字串寫入至登錄。 容器應用程式會使用此字串來建立控制項的實例。

   根據預設，控制項類型識別碼是以您在 [**新增專案**] 對話方塊中所指定的專案名稱和簡短名稱為基礎。 此名稱應符合類型名稱。

   根據預設，控制項類型識別碼會如下所示：

   *專案名稱. 簡短名稱*Ctrl. 1

   如果您變更此對話方塊中的簡短名稱，控制項類型識別碼會如下所示：

   *專案名稱. NewShortName*Ctrl. 1

- **PropPage 類別名稱**

   根據預設，屬性頁類別的名稱是以簡短名稱為依據，並以 `C` 做為前置詞，`PropPage` 做為尾碼。 例如，如果 `Price`控制項的簡短名稱，則會 `CPricePropPage`屬性頁類別名稱。 這個名稱應該符合控制項類別名稱，並以 `PropPage`附加。

- **PropPage .h 檔案**

   根據預設，屬性頁標頭檔的名稱是以簡短名稱為依據，並以 `PropPage` 做為尾碼，`.h` 做為副檔名。 例如，如果 `Price`控制項的簡短名稱，則屬性頁標題檔案名會是 `PricePropPage.h`。 此名稱應符合類別名稱。

- **PropPage .cpp 檔案**

   根據預設，屬性頁執行檔案的名稱是以簡短名稱為依據，並以 `PropPage` 做為尾碼，`.cpp` 做為副檔名。 例如，如果 `Price`控制項的簡短名稱，則屬性頁標題檔案名會是 `PricePropPage.cpp`。 這個名稱應該與標頭檔名稱相符。

- **PropPage 類型名稱**

   根據預設，屬性頁的類型名稱是以簡短名稱為基礎，後面接著 `Property Page`。 例如，如果 `Price`控制項的簡短名稱，則會 `Price Property Page`屬性頁類型名稱。 如果您變更此欄位中的值，請確定 [名稱] 指出控制項類別。

- **PropPage 類型識別碼**

   設定屬性頁類別的識別碼。 當控制項套用至專案時，控制項會將此字串寫入登錄中。 容器應用程式會使用此字串來建立控制項屬性頁的實例。

   根據預設，屬性頁的類型識別碼是以 [**新增專案**] 對話方塊中所指定的專案名稱和簡短名稱為基礎。 此名稱應符合類型名稱。

   根據預設，屬性頁的類型識別碼會如下所示：

   *專案名稱. 簡短名稱*PropPage。1

   如果您變更此對話方塊中的簡短名稱，屬性頁的類型識別碼會如下所示：

   *專案名稱. NewShortName*PropPage。1

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控制項精靈、應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控制項精靈、控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)
