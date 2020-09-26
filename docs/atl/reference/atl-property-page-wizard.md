---
title: ATL 屬性頁精靈
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: c25e3b9194cf0c7dc7c152edb50be01def2d2d9b
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352723"
---
# <a name="atl-property-page-wizard"></a>ATL 屬性頁精靈

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供此精靈。

::: moniker-end

::: moniker range="<=vs-2017"

此精靈會[將屬性頁加入至 ATL 專案](../../atl/reference/adding-an-atl-property-page.md)或含 ATL 支援的 MFC 專案。 ATL 屬性頁提供使用者介面，可用來設定一或多個 COM 物件的屬性 (或呼叫方法)。

## <a name="remarks"></a>備註

從 Visual Studio 2008 開始，此精靈所產生的註冊指令碼將會在 **HKEY_CURRENT_USER** 而非 **HKEY_LOCAL_MACHINE** 下方註冊它的 COM 元件。 若要修改此行為，請設定 ATL 精靈的 [為所有使用者註冊元件]**** 選項。

## <a name="names"></a>名稱

指定要新增至專案的物件、介面和類別名稱。 除了**簡短名稱**，所有其他方塊均可單獨編輯。 如果您變更**簡短名稱**的文字，該變更即會反映於此頁面的所有其他方塊名稱中。 如果您在 [COM] 區段中變更 **Coclass** 名稱，則變更會反映於 [型別]**** 和 [ProgID]**** 方塊中。 此命名行為旨在讓您開發屬性頁時，能夠輕鬆地識別所有名稱。

> [!NOTE]
> **Coclass** 只能在未使用屬性的專案上進行編輯。 如果您的專案會使用屬性，則您無法編輯 **Coclass**。

### <a name="c"></a>C++

提供建立來實作物件的 C++ 類別相關資訊。

|詞彙|定義|
|-|-|
|**簡短名稱**|設定物件的縮寫名稱。 您提供的名稱可決定類別和 **Coclass** 名稱、檔案 (**.cpp** 和 **.h**) 名稱、**型別**名稱，以及 **ProgID** (但前提是您並未個別變更這些欄位)。|
|**.h 檔案**|設定新物件類別的標頭檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案，在您按一下精靈中的 [完成]**** 之前，精靈不會將它儲存至選取的位置。<br /><br /> 精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。|
|**類別**|設定實作物件的類別名稱。 此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎，前面加上 'C'，此為類別名稱的一般前置詞。|
|**.cpp 檔案**|設定新物件類別的實作檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成]**** 之前，檔案不會儲存至選取的位置。<br /><br /> 精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。|
|**使用屬性**|指出物件是否會使用屬性。 如果您要將物件加入至使用屬性的 ATL 專案，則要選取此選項且無法變更，也就是，您只能將使用屬性的物件加入至使用屬性支援所建立的專案。<br /><br /> 您只能將使用屬性的物件加入至使用屬性的 ATL 專案。 如果您針對不含屬性支援的 ATL 專案選取此選項，精靈會提示您指定是否要將屬性支援加入至專案。<br /><br /> 根據預設，在您設定此選項後加入的任何物件都會指定為使用屬性 (已選取核取方塊)。 您可以清除此方塊以加入未使用屬性的物件。<br /><br /> 如需詳細資訊，請參閱 [應用程式設定、ATL 專案嚮導](../../atl/reference/application-settings-atl-project-wizard.md) 和 [屬性的基本機制](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) 。|

### <a name="com"></a>COM

提供物件 COM 功能的相關資訊。

- **元件類**

   設定元件類別的名稱，其中包含物件所支援的介面清單。

   > [!NOTE]
   > 如果您使用屬性 (Attribute) 建立專案，或者，如果您在此精靈頁面中指出屬性 (Property) 頁會使用屬性 (Attribute)，您就無法變更此選項，因為 ATL 未包含 `coclass` 屬性 (Attribute)。

- **型別**

   設定將出現在登錄中的物件描述

- **ProgID**

   設定容器可使用的名稱，而不是物件的 CLSID。

::: moniker-end

## <a name="see-also"></a>另請參閱

[選項，ATL 屬性頁精靈](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[字串，ATL 屬性頁精靈](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[範例：執行屬性頁](../../atl/example-implementing-a-property-page.md)
