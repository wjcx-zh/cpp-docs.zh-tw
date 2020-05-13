---
title: ATL 控制項精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321703"
---
# <a name="atl-control-wizard"></a>ATL 控制項精靈

插入 ATL 專案(或支援 ATL 的 MFC 專案)的 ATL 控制項。 您可以使用此精靈插入三種控制項之一:

- 標準控制

- 複合控制

- DHTML 控制項

此外,還可以指定最小控制項,從[「介面」](../../atl/reference/interfaces-atl-control-wizard.md)清單中刪除介面,這些介面作為預設功能提供,供控制項在大多數容器中打開。 您可以在精靈的 **「介面」** 頁中為控制項設定所需的控制項支援的介面。

## <a name="remarks"></a>備註

此嚮導生成的註冊腳本將在HKEY_CURRENT_USER下註冊其 COM 元件,而不是HKEY_LOCAL_MACHINE。 若要修改此行為，請設定 ATL 精靈的 [為所有使用者註冊元件]**** 選項。

## <a name="names"></a>Names

指定要新增至專案的物件、介面和類別名稱。 除**短名稱**外,所有其他框都可以獨立更改。 如果您變更**簡短名稱**的文字，該變更即會反映於此頁面的所有其他方塊名稱中。 如果在 COM 部份中更改**Coclass**名稱,則更改將反映在 **「類型」** 框中,但 **「介面**名稱」 和 **「ProgID」** 不會更改。 此命名行為旨在讓您開發控制項時，能夠輕鬆地識別所有名稱。

> [!NOTE]
> **Coclass**僅在非屬性化控制項上編輯。 如果您的專案會使用屬性，則您無法編輯 **Coclass**。

### <a name="c"></a>C++

提供建立來實作物件的 C++ 類別相關資訊。

- **簡短名稱**

   設定物件的縮寫名稱。 您提供的名稱確定類和**Coclass**名稱、檔 (。CPP 與 。H) 名稱、介面名稱和**Type**名稱,除非您單獨更改這些欄位。

- **類別**

   設定實作物件的類別名稱。 此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎，前面加上 'C'，此為類別名稱的一般前置詞。

- **.h 檔案**

   設定新物件類別的標頭檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果選擇現有檔,嚮導不會將其保存到所選位置,直到按一**下 「完成**」。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

   設定新物件類別的實作檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成]**** 之前，檔案不會儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。

- **使用屬性**

   指出物件是否會使用屬性。 如果您要將物件新增至屬性化的 ATL 專案，則此選項已選取且無法變更。 也就是說，您只能將屬性化的物件新增至透過屬性支援建立的專案。

   您只能將使用屬性的物件加入至使用屬性的 ATL 專案。 如果您針對不含屬性支援的 ATL 專案選取此選項，精靈會提示您指定是否要將屬性支援加入至專案。

   根據預設，在您設定此選項後加入的任何物件都會指定為使用屬性 (已選取核取方塊)。 您可以清除此方塊以加入未使用屬性的物件。

   如需詳細資訊，請參閱[應用程式設定，ATL 專案精靈](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)。

### <a name="com"></a>COM

提供物件 COM 功能的相關資訊。

- **Coclass**

   設定元件類別的名稱，其中包含物件所支援的介面清單。

   > [!NOTE]
   > 如果使用屬性創建專案,或者在此嚮導頁上指示控制項使用屬性,則無法更改此選項,因為 ATL 不包括**coclass**屬性。

- **介面**

   設置物件的介面的名稱。 默認情況下,介面名稱以"I"為預寫。

- **型別**

   設定將出現在登錄中的物件描述

- **ProgID**

   設定容器可使用的名稱，而不是物件的 CLSID。 此欄位不會自動填充。 如果不手動填充此欄位,則控件可能不適用於其他工具。 例如,在 **『插入 ActiveX 控制件**』`ProgID`對話框中,沒有生成的 ActiveX 控制項不可用。 如需對話方塊的詳細資訊，請參閱[插入 ActiveX 控制項對話方塊](../../windows/insert-activex-control-dialog-box.md)。

## <a name="see-also"></a>另請參閱

[ATL 控制項](../../atl/reference/adding-an-atl-control.md)<br/>
[新增組合的控制項](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 物件的基礎知識](../../atl/fundamentals-of-atl-com-objects.md)
