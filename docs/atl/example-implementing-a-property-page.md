---
title: 實作屬性頁 (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 68b4aaef06e40a8ec7b00f9ba744d83ce3388da2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492386"
---
# <a name="example-implementing-a-property-page"></a>範例：實作屬性頁

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL 屬性頁精靈。

::: moniker-end

::: moniker range="<=vs-2017"

此範例示範如何建置可顯示 (並可讓您變更) [文件類別](../mfc/document-classes.md)介面屬性的屬性頁。

此範例是以 [ATLPages 範例](../overview/visual-cpp-samples.md)為基礎。

若要完成此範例，您將會：

- 使用 [新增類別] 對話方塊和 ATL 屬性頁精靈，[新增 ATL 屬性頁類別](#vcconusing_the_atl_object_wizard)。

- 加入 `Document` 介面有趣屬性的新控制項以[編輯對話方塊資源](#vcconediting_the_dialog_resource)。

- [新增訊息處理常式](#vcconadding_message_handlers)以保留通知使用者所做變更的屬性頁網站。

- 在 [Housekeeping](#vcconhousekeeping) 區段中加入一些 `#import` 陳述式和 Typedef。

- [覆寫 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) 可驗證傳遞至屬性頁的物件。

- [覆寫 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) 可初始化屬性頁的介面。

- [覆寫 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) 可將物件更新為最新的屬性值。

- 建立簡單的協助程式物件可[顯示屬性頁](#vccontesting_the_property_page)。

- [建立巨集](#vcconcreating_a_macro)，此巨集將測試屬性頁。

##  <a name="vcconusing_the_atl_object_wizard"></a> 新增 ATL 屬性頁類別

首先，為 DLL 伺服器建立一個稱為 `ATLPages7` 的新 ATL 專案。 現在，使用 [ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md)產生屬性頁。 為屬性頁提供一個 **DocProperties** 的**簡短名稱**，然後切換到 [字串]頁面，以設定屬性頁面專屬的項目，如下表所示。

|項目|值|
|----------|-----------|
|標題|TextDocument|
|Doc 字串|VCUE TextDocument 屬性|
|Helpfile|*\<blank>*|

您在這個精靈頁面上設定的值將會在呼叫 `IPropertyPage::GetPageInfo` 時，傳回至屬性頁容器。 字串在此之後發生的變化取決於容器，但通常用來向使用者識別您的頁面。 Title 通常會在出現您頁面上方的索引標籤中，而 Doc 字串則可能會顯示在狀態列或工具提示中 (但標準屬性框架完全不會使用此字串)。

> [!NOTE]
>  精靈會將您在此處設定的字串儲存為您專案中的字串資源。 如果您需要在產生頁面的程式碼之後變更此資訊，您可以使用資源編輯器，輕鬆地編輯這些字串。

按一下 [確定]，讓精靈產生屬性頁。

##  <a name="vcconediting_the_dialog_resource"></a> 編輯對話方塊資源

既然已經產生屬性頁，您必須將幾個控制項新增至代表您頁面的對話方塊資源。 新增編輯方塊、靜態文字控制項以及核取方塊，並設定其識別碼，如下所示：

![編輯對話方塊資源](../atl/media/ppgresourcelabeled.gif "編輯對話方塊資源")

這些控制項將用來顯示文件的檔案名稱及其唯讀狀態。

> [!NOTE]
>  對話方塊資源不包含框架或命令按鈕，也沒有您可能預期的索引標籤式外觀。 屬性頁框架會提供這些功能，例如，透過呼叫 [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe) 建立的功能。

##  <a name="vcconadding_message_handlers"></a> 加入訊息處理常式

利用適當的控制項，您可以加入訊息處理常式，以便在任一個控制項的值變更時，更新頁面的已變更狀態：

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

此程式碼會呼叫 [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) 以回應對編輯控制項或核取方塊所做的變更，如此會通知頁面網站頁面已變更。 頁面網站通常會透過啟用或停用屬性頁框架上的的 [套用] 按鈕來回應。

> [!NOTE]
>  在您自己的屬性頁中，您可能需要精確地追蹤使用者已經變更哪些屬性，讓您可以避免更新未曾變更的屬性。 此範例會追蹤原始屬性值，並在套用變更時將原始屬性值與來自 UI 的目前值相比較，藉此實作該程式碼。

##  <a name="vcconhousekeeping"></a> 內務處理

現在將一些 `#import` 陳述式加入至 DocProperties.h，讓編譯器了解 `Document` 介面：

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

您也需要參考 `IPropertyPageImpl` 基底類別；將下列 **typedef** 新增到 `CDocProperties` 類別：

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 覆寫 IPropertyPageImpl::SetObjects

您需要覆寫的第一個 `IPropertyPageImpl` 方法是 [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)。 您將在此處加入程式碼來檢查是否只傳遞了單一物件，且其支援您預期的 `Document` 介面：

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  對此頁面而言，僅支援單一物件很合理，因為您將允許使用者設定物件的檔案名稱，而且任何一個位置只能存在一個檔案。

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 覆寫 IPropertyPageImpl::Activate

下一步是在頁面第一次建立時，使用基礎物件的屬性值初始化屬性頁。

在此情況下，您應該將下列成員新增至類別，因為您也會在頁面的使用者套用其變更時，使用初始屬性值進行比較：

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

[Activate](../atl/reference/ipropertypageimpl-class.md#activate) 方法的基底類別實作會負責建立對話方塊及其控制項，因此您可以覆寫此方法，並在呼叫基底類別之後加入您自己的初始化：

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

此程式碼使用 `Document` 介面的 COM 方法，以取得您感興趣的屬性。 接著，它會使用 [CDialogImpl](../atl/reference/cdialogimpl-class.md) 所提供的 Win32 API 包裝函式及其基底類別，向使用者顯示屬性值。

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 覆寫 IPropertyPageImpl::Apply

當使用者想要將其變更套用至物件時，屬性頁網站將會呼叫 [Apply](../atl/reference/ipropertypageimpl-class.md#apply) 方法。 這是在 `Activate` 中反向執行程式碼的位置。`Activate` 會接受物件中的值，並其推送到屬性頁上的控制項，而 `Apply` 則會接受屬性頁上控制項的值，並將其推送到物件。

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  在此實作一開始，針對 [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) 的檢查是為了在多次呼叫 `Apply` 時，避免不必要的物件更新所進行的。 系統也會針對每個屬性值進行檢查，以確保只有變更會導致對 `Document` 進行方法呼叫。

> [!NOTE]
> `Document` 會將 `FullName` 當作唯讀屬性公開。 若要根據對屬性頁所做的變更來更新文件的檔案名稱，您必須使用 `Save` 方法，使用不同的名稱儲存檔案。 因此，屬性頁中的程式碼不必限制自己取得或設定屬性。

##  <a name="vccontesting_the_property_page"></a> 顯示屬性頁

若要顯示此頁面，您需要建立一個簡單的協助程式物件。 協助程式物件會提供一種簡化 `OleCreatePropertyFrame` API 的方法，以顯示連接到單一物件的單一頁面。 此協助程式將經過設計，因此可以從 Visual Basic 使用它。

使用 [[加入類別對話方塊]](../ide/add-class-dialog-box.md) 和 [[ATL 簡單物件精靈]](../atl/reference/atl-simple-object-wizard.md) 產生新的類別，並使用 `Helper` 作為其簡短名稱。 建立之後，加入一個方法，如下表所示。

|項目|值|
|----------|-----------|
|方法名稱|`ShowPage`|
|參數|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*bstrCaption* 參數是要顯示為對話方塊標題的標題。 *bstrID* 參數是一個字串，代表要顯示之屬性頁的 CLSID 或 ProgID。 *pUnk* 參數將會是屬性頁會設定其屬性之物件的 `IUnknown` 指標。

實作方法，如下所示：

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> 建立巨集

一旦建置專案之後，您可以使用您在 Visual Studio 開發環境中建立並執行的簡單巨集，測試屬性頁和協助程式物件。 此巨集將會建立一個協助程式物件，然後使用 **DocProperties** 屬性頁的 ProgID，以及目前在 Visual Studio 編輯器內作用中之文件的 `IUnknown` 指標，呼叫其 `ShowPage` 方法。 此巨集所需要的程式碼如下所示：

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

當您執行此巨集時，將會顯示屬性頁，其中會顯示目前作用中之文字文件的檔案名稱和唯讀狀態。 文件的唯讀狀態只會反映是否能夠寫入至開發環境中的文件；它不會影響磁碟上檔案的唯讀屬性。

::: moniker-end

## <a name="see-also"></a>另請參閱

[屬性頁](../atl/atl-com-property-pages.md)<br/>
[ATLPages 範例](../overview/visual-cpp-samples.md)
