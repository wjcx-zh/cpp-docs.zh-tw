---
title: 實作屬性頁 (ATL)
ms.date: 11/19/2018
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 9aaf75916196f33904a51289d0a49725e042aa9e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777034"
---
# <a name="example-implementing-a-property-page"></a>範例：實作屬性頁

此範例示範如何建置會顯示 （並可讓您變更） 的屬性的屬性頁[文件類別](../mfc/document-classes.md)介面。

範例根據[ATLPages 範例](../overview/visual-cpp-samples.md)。

若要完成此範例中，您將會：

- [新增 ATL 屬性頁類別](#vcconusing_the_atl_object_wizard)使用 [加入類別] 對話方塊中，ATL 屬性頁精靈。

- [編輯對話方塊資源](#vcconediting_the_dialog_resource)藉由加入新控制項的有趣屬性`Document`介面。

- [新增訊息處理常式](#vcconadding_message_handlers)保留屬性頁面網站通知的使用者所做的變更。

- 新增一些`#import`陳述式，並在 typedef [Housekeeping](#vcconhousekeeping)一節。

- [覆寫 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects)驗證傳遞至屬性頁的物件。

- [覆寫 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate)初始化屬性頁的介面。

- [覆寫 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply)更新物件的最新的屬性值。

- [顯示屬性頁](#vccontesting_the_property_page)藉由建立簡單的協助程式物件。

- [建立巨集](#vcconcreating_a_macro)，將測試屬性頁。

##  <a name="vcconusing_the_atl_object_wizard"></a> 新增 ATL 屬性頁類別

首先，建立新的 ATL 專案呼叫的 DLL 伺服器`ATLPages7`。 現在，使用[ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md)產生屬性頁。 讓屬性頁**簡短名稱**的**DocProperties**然後切換到**字串**頁面，即可設定屬性頁面特定的項目下, 表所示。

|項目|值|
|----------|-----------|
|標題|TextDocument|
|文件字串|VCUE TextDocument 屬性|
|Helpfile|*\<blank>*|

您在精靈的這個頁面設定的值會傳回至屬性頁的容器時它會呼叫`IPropertyPage::GetPageInfo`。 會發生什麼事字串之後，仍取決於容器中，但通常用來識別您使用者的頁面。 標題通常會在您的頁面上方的索引標籤中，文件字串可能會顯示在狀態列上或工具提示 （儘管標準屬性框架完全不使用此字串）。

> [!NOTE]
>  您在此處設定的字串會儲存精靈為您的專案中的字串資源。 您可以輕鬆地編輯這些字串時，使用資源編輯器，如果您需要您頁面的程式碼產生之後變更這項資訊。

按一下 **確定**，使精靈可產生屬性頁。

##  <a name="vcconediting_the_dialog_resource"></a> 編輯對話方塊資源

現在，已產生內容頁，您必須將幾個控制項新增至對話方塊資源，其代表您的頁面。 新增編輯方塊、 靜態文字控制項，並核取方塊，並設定其識別碼，如下所示：

![編輯對話方塊資源](../atl/media/ppgresourcelabeled.gif "編輯對話方塊資源")

這些控制項將用來顯示文件和其唯讀狀態的檔案名稱中。

> [!NOTE]
>  對話方塊資源不包含框架或命令的按鈕，也沒有您可能預期的索引標籤的外觀。 這些功能可提供透過呼叫來建立類似的屬性頁面外框[OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe)。

##  <a name="vcconadding_message_handlers"></a> 加入訊息處理常式

的地方使用控制項，您可以新增至任一控制項的值變更時更新頁面的已變更的狀態訊息處理常式：

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

此程式碼會藉由呼叫編輯控制項或核取方塊所做的變更回應[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)，而這會通知頁面已變更頁面網站。 頁面網站會回應啟用或停用的通常**套用**屬性頁面框架上的按鈕。

> [!NOTE]
>  在您自己的屬性頁，您可能需要來追蹤精確的屬性已經更改由使用者，讓您可以避免更新未曾變更的屬性。 此範例中實作該程式碼的原始屬性值追蹤並比較這些最新的值，從 UI，它會在套用變更時。

##  <a name="vcconhousekeeping"></a> 清理

現在加入幾個`#import`DocProperties.h 陳述式，讓編譯器知道`Document`介面：

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

您也需要是指`IPropertyPageImpl`基底類別，新增下列**typedef**到`CDocProperties`類別：

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 覆寫 IPropertyPageImpl::SetObjects

第一個`IPropertyPageImpl`方法，您需要覆寫[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)。 您將在此處新增程式碼來檢查已傳遞單一物件，且其支援`Document`您預期的介面：

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  必須對這個頁面支援只有單一物件，因為您要允許使用者設定物件的檔案名稱，只能有一個檔案可以存在於任何一個位置。

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 覆寫 IPropertyPageImpl::Activate

下一步是初始化與基礎物件的屬性值的 [屬性] 頁面，頁面第一次建立時。

在此情況下您應該將下列成員加入至類別，因為您也會使用的初始屬性值進行比較時的頁面使用者套用其變更：

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

基底類別實作[Activate](../atl/reference/ipropertypageimpl-class.md#activate)方法會負責建立對話方塊和其控制項，讓您可以覆寫這個方法，並加入您自己的初始設定之後呼叫的基底類別：

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

此程式碼使用的 COM 方法`Document`介面，以取得您感興趣的屬性。 然後它會使用所提供的 Win32 API 包裝函式[CDialogImpl](../atl/reference/cdialogimpl-class.md)及其基底類別，以向使用者顯示的屬性值。

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 覆寫 IPropertyPageImpl::Apply

當使用者想要將其變更套用至物件時，會呼叫屬性頁站台[套用](../atl/reference/ipropertypageimpl-class.md#apply)方法。 這是執行中的程式碼相反的地方`Activate`，而`Activate`花了物件中的值，並它們推送到 [屬性] 頁面上的控制項`Apply`接受的值從 [屬性] 頁面上的控制項，並將其推送物件。

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  對照檢查[m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty)開頭的這項實作是為了避免不必要更新的物件，如果初始檢查`Apply`呼叫一次以上。 也有針對每個屬性值，以確保所做的變更會導致方法呼叫來檢查`Document`。

> [!NOTE]
> `Document` 會公開`FullName`為唯讀屬性。 若要更新屬性頁所做的變更為基礎的文件的檔案名稱，您必須使用`Save`方法，將檔案儲存使用不同的名稱。 因此，若要限制本身沒有屬性頁中的程式碼來取得或設定屬性。

##  <a name="vccontesting_the_property_page"></a> 顯示屬性頁

若要顯示此頁面，您要建立簡單的協助程式物件。 協助程式物件會提供方法，可簡化`OleCreatePropertyFrame`顯示單一頁面的 API 連線到單一物件。 將設計此協助程式，以便可以從 Visual Basic 使用它。

使用[加入類別對話方塊](../ide/add-class-dialog-box.md)並[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)產生新的類別，並使用`Helper`做為其簡短名稱。 建立之後，新增方法下, 表所示。

|項目|值|
|----------|-----------|
|方法名稱|`ShowPage`|
|參數|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*BstrCaption*參數是要顯示為對話方塊的標題的標題。 *BstrID*參數是字串，表示為 CLSID 或 ProgID 屬性頁的顯示。 *PUnk*參數將會是`IUnknown`屬性頁會設定其屬性之物件的指標。

實作方法，如下所示：

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> 建立巨集

一旦建置專案，您可以測試屬性頁，並使用簡單的巨集，您可以建立並執行 Visual Studio 開發環境中的協助程式物件。 這個巨集將會建立協助程式物件，然後呼叫其`ShowPage`方法使用的 ProgID **DocProperties**  屬性頁和`IUnknown`目前使用 Visual Studio 編輯器中的文件的指標。 您需要為這個巨集的程式碼如下所示：

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

當您執行這個巨集時，會顯示檔案名稱和目前作用中的文字文件的唯讀狀態顯示 [屬性] 頁面。 文件的唯讀狀態只會反映文件在開發環境中，寫入的能力它不會影響磁碟上檔案的唯讀屬性。

## <a name="see-also"></a>另請參閱

[屬性頁](../atl/atl-com-property-pages.md)<br/>
[ATLPages 範例](../overview/visual-cpp-samples.md)
