---
title: ATL OLE DB 提供者精靈
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 1b30b9aa3956d0dbfa7ddf2fe7281484ebd2444e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524664"
---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 提供者精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="vs-2017"

## <a name="remarks"></a>備註

從 Visual Studio 2008 開始，此精靈所產生的註冊指令碼將會在 **HKEY_CURRENT_USER** 而非 **HKEY_LOCAL_MACHINE** 下方註冊它的 COM 元件。 若要修改此行為，請設定 ATL 精靈的 [為所有使用者註冊元件] 選項。

下表描述適用於 ATL OLE DB 提供者精靈的選項：

- **簡短名稱**

   輸入要建立之提供者的簡短名稱。 系統將根據您在此處輸入的內容，自動填入精靈中的其他編輯方塊。 您可以視需要編輯其他名稱方塊。

- **Coclass**

   Coclass 的名稱。 ProgID 名稱將變更以符合此名稱。

- **使用屬性**

   這個選項會指定精靈是否將使用屬性或範本宣告來建立提供者類別。 當您選取此選項時，精靈會使用屬性而非範本宣告 (如果您已建立使用屬性的專案，則此為預設選項)。 當您清除此選項時，精靈會使用範本宣告而非屬性 (如果您已建立未使用屬性的專案，則此為預設選項)。

   如果您在建立未使用屬性的專案時選取此選項，精靈就會警告您專案將轉換為使用屬性的專案，並詢問您是否要繼續進行。

- **ProgID**

   Prog ID (或程式設計識別碼) 是應用程式可用來代替 GUID 的文字字串。 ProgID 名稱的格式為 *Projectname.Coclassname*。

- **版本**

   提供者的版本號碼。 預設為 1。

- **資料來源類別**

   資料來源類別的名稱，格式為 C*Shortname*Source。

- **資料來源 .h 檔案**

   資料來源類別的標頭檔。 您可以編輯這個檔案的名稱或選取現有的標頭檔。

- **工作階段類別**

   工作階段類別的名稱，格式為 C*Shortname*Session。

- **工作階段 .h 檔案**

   工作階段類別的標頭檔。 您可以編輯這個檔案的名稱或選取現有的標頭檔。

- **命令類別**

   命令類別的名稱，格式為 C*Shortname*Command。

- **命令 .h 檔案**

   命令類別的標頭檔。 此名稱無法編輯且取決於資料列集標頭檔的名稱。

- **資料列集類別**

   資料列集類別的名稱，格式為 C*Shortname*Rowset。

- **資料列集 .h 檔案**

   資料列集類別的標頭檔。 您可以編輯這個檔案的名稱或選取現有的標頭檔。

- **資料列集 .cpp 檔案**

   提供者的實作檔案。 您可以編輯這個檔案的名稱或選取現有的實作檔。

::: moniker-end

## <a name="see-also"></a>另請參閱

[ATL OLE DB 提供者](../../atl/reference/adding-an-atl-ole-db-provider.md)
