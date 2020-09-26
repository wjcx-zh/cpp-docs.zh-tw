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
ms.openlocfilehash: c89fe17272399212e4436481abc2800c3ab6e660
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353138"
---
# <a name="atl-control-wizard"></a>ATL 控制項精靈

插入 ATL 專案 (或具有 atl 支援) ATL 控制項的 MFC 專案。 您可以使用此嚮導插入三種控制項中的其中一種：

- 標準控制項

- 複合控制項

- DHTML 控制項

此外，您可以指定最基本的控制項，從 [介面](../../atl/reference/interfaces-atl-control-wizard.md) 清單中移除介面，這些介面會提供做為在大部分容器中開啟之控制項的預設值。 您可以在嚮導的 [ **介面** ] 頁面中，設定您要支援的控制項介面。

## <a name="remarks"></a>備註

此 wizard 所產生的註冊腳本將會在 HKEY_CURRENT_USER 下註冊其 COM 元件，而不是 HKEY_LOCAL_MACHINE。 若要修改此行為，請設定 ATL 精靈的 [為所有使用者註冊元件]**** 選項。

## <a name="names"></a>名稱

指定要新增至專案的物件、介面和類別名稱。 除了 **簡短名稱**之外，其他所有方塊也可以獨立變更。 如果您變更**簡短名稱**的文字，該變更即會反映於此頁面的所有其他方塊名稱中。 如果您在 [COM] 區段中變更 **Coclass** 名稱，則變更會反映在 [ **類型** ] 方塊中，但 **介面** 名稱和 **ProgID** 不會變更。 此命名行為旨在讓您開發控制項時，能夠輕鬆地識別所有名稱。

> [!NOTE]
> **Coclass** 只能在非特性化控制項上進行編輯。 如果您的專案會使用屬性，則您無法編輯 **Coclass**。

### <a name="c"></a>C++

提供建立來實作物件的 C++ 類別相關資訊。

- **簡短名稱**

   設定物件的縮寫名稱。 您所提供的名稱會決定類別和 **Coclass** 名稱，也就是檔案 (。CPP 和。H) 名稱、介面名稱和 **類型** 名稱，除非您個別變更這些欄位。

- **類別**

   設定實作物件的類別名稱。 此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎，前面加上 'C'，此為類別名稱的一般前置詞。

- **.h 檔案**

   設定新物件類別的標頭檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選取現有的檔案，則在您按一下 **[完成**] 之前，嚮導將不會將它儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

   設定新物件類別的實作檔名稱。 根據預設，此名稱會以您在 [簡短名稱]**** 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成]**** 之前，檔案不會儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成]**** 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是]**** 可附加檔案，按一下 [否]**** 可返回精靈並指定另一個檔案名稱。

- **使用屬性**

   指出物件是否會使用屬性。 如果您要將物件新增至屬性化的 ATL 專案，則此選項已選取且無法變更。 也就是說，您只能將屬性化的物件新增至透過屬性支援建立的專案。

   您只能將使用屬性的物件加入至使用屬性的 ATL 專案。 如果您針對不含屬性支援的 ATL 專案選取此選項，精靈會提示您指定是否要將屬性支援加入至專案。

   根據預設，在您設定此選項後加入的任何物件都會指定為使用屬性 (已選取核取方塊)。 您可以清除此方塊以加入未使用屬性的物件。

   如需詳細資訊，請參閱 [應用程式設定、ATL 專案嚮導](../../atl/reference/application-settings-atl-project-wizard.md) 和 [屬性的基本機制](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) 。

### <a name="com"></a>COM

提供物件 COM 功能的相關資訊。

- **元件類**

   設定元件類別的名稱，其中包含物件所支援的介面清單。

   > [!NOTE]
   > 如果您使用屬性來建立專案，或在這個 wizard 頁面上指出控制項使用屬性，您就無法變更此選項，因為 ATL 不包含 **coclass** 屬性。

- **介面**

   設定物件的介面名稱。 依預設，介面名稱前面會加上 "I"。

- **型別**

   設定將出現在登錄中的物件描述

- **ProgID**

   設定容器可使用的名稱，而不是物件的 CLSID。 此欄位不會自動填入。 如果您未手動填入此欄位，其他工具可能無法使用該控制項。 例如，在沒有的情況下產生的 ActiveX 控制項， `ProgID` 在 [ **插入 activex 控制項** ] 對話方塊中無法使用。 如需對話方塊的詳細資訊，請參閱 [插入 ActiveX 控制項](../../windows/adding-editing-or-deleting-controls.md#insert-activex-controls)。

## <a name="see-also"></a>另請參閱

[ATL 控制項](../../atl/reference/adding-an-atl-control.md)<br/>
[將功能新增至複合控制項](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)
