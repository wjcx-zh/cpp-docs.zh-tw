---
title: 實作屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 49058fe13457c2d0050452cbc0015575371e4043
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706910"
---
# <a name="implementing-property-pages"></a>實作屬性頁

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL 屬性頁精靈。

::: moniker-end

::: moniker range="<=vs-2017"

屬性頁是實作 `IPropertyPage` 或 `IPropertyPage2` 介面的 COM 物件。 ATL 支援透過 [[加入類別對話方塊]](../ide/add-class-dialog-box.md) 中的 [[ATL 屬性頁精靈]](../atl/reference/atl-property-page-wizard.md)，實作屬性頁。

若要使用 ATL 建立屬性頁：

- 建立或開啟 ATL 動態連結程式庫 (DLL) 伺服器專案。

- 開啟 [[加入類別對話方塊]](../ide/add-class-dialog-box.md)，然後選取 [ATL 屬性頁]。

- 請確定您的屬性頁是 Apartment 執行緒 (因為它有使用者介面)。

- 設定與您的頁面相關聯的標題、描述 (Doc 字串) 以及說明檔。

- 將控制項加入至產生的對話方塊資源，作為您屬性頁面的使用者介面。

- 回應您頁面使用者介面中的變更，以執行驗證、更新頁面網站，或更新與您的頁面相關聯的物件。 特別是，當使用者對屬性頁進行變更時，請呼叫 [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)。

- 或者，選擇性地使用以下的指導方針覆寫 `IPropertyPageImpl` 方法。

   |IPropertyPageImpl 方法|當您要執行下列操作時覆寫...|注意|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|針對要傳遞至您頁面及其所支援之介面的物件數目，執行基本的例行性檢查。|再呼叫基底類別實作之前，請執行您自己的程式碼。 如果所設定的物件不符合您的預期，您應該儘速使呼叫失敗。|
   |[Activate](../atl/reference/ipropertypageimpl-class.md#activate)|初始化您頁面的使用者介面 (例如，使用物件中目前的屬性值設定對話方塊控制項、動態建立控制項，或執行其他初始化)。|在您的程式碼之前呼叫基底類別實作，讓基底類別有機會在您嘗試更新它們之前，建立對話方塊視窗和所有控制項。|
   |[Apply](../atl/reference/ipropertypageimpl-class.md#apply)|驗證屬性設定，並更新物件。|不需要呼叫基底類別實作，因為除了追蹤呼叫之外，它不會執行任何操作。|
   |[Deactivate](../atl/reference/ipropertypageimpl-class.md#deactivate)|清除與視窗相關的項目。|基底類別實作會終結代表屬性頁的對話方塊。 如果您需要在終結對話方塊之前清除，您應該在呼叫基底類別之前加入程式碼。|

如需範例屬性頁實作，請參閱[範例：實作屬性頁](../atl/example-implementing-a-property-page.md)。

> [!NOTE]
> 如果您想要在屬性頁中裝載 ActiveX 控制項，必須變更您精靈產生之類別的衍生。 將 **CDialogImpl\<CYourClass >** 取代為基底類別清單中的 **CAxDialogImpl\<CYourClass >**。

::: moniker-end

## <a name="see-also"></a>另請參閱

[屬性頁](../atl/atl-com-property-pages.md)<br/>
[ATLPages 範例](../overview/visual-cpp-samples.md)
