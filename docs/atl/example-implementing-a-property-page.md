---
title: "實作屬性頁 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96314b4b8ba7696f784354c2353070ca3873c11c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="example-implementing-a-property-page"></a>範例： 實作屬性頁
這個範例示範如何建置會顯示 （並可讓您變更） 的屬性的屬性頁[文件類別](../mfc/document-classes.md)介面。  
  
 範例根據[ATLPages 範例](../visual-cpp-samples.md)。  
  
 若要完成此範例中，您將能夠：  
  
- [加入 ATL 屬性頁類別](#vcconusing_the_atl_object_wizard)使用加入類別對話方塊和 ATL 屬性頁精靈。  
  
- [編輯對話方塊資源](#vcconediting_the_dialog_resource)透過加入新的控制項屬性的有趣**文件**介面。  
  
- [加入訊息處理常式](#vcconadding_message_handlers)保留屬性頁站台通知的使用者所做的變更。  
  
-   新增一些`#import`陳述式和在 typedef[環境維護](#vcconhousekeeping)> 一節。  
  
- [覆寫 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects)驗證傳遞至屬性頁的物件。  
  
- [覆寫 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate)初始化屬性頁的介面。  
  
- [覆寫 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply)更新物件的最新的屬性值。  
  
- [顯示屬性頁](#vccontesting_the_property_page)藉由建立簡單的協助程式物件。  
  
- [建立巨集](#vcconcreating_a_macro)，將測試屬性頁。  
  
##  <a name="vcconusing_the_atl_object_wizard"></a>加入 ATL 屬性頁類別  
 首先，建立新的 ATL 專案呼叫的 DLL 伺服器`ATLPages7`。 現在使用[ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md)產生屬性頁。 提供屬性頁**簡短名稱**的**DocProperties**然後切換到**字串**頁面設定屬性頁面特定項目，如下表所示。  
  
|項目|值|  
|----------|-----------|  
|標題|TextDocument|  
|文件字串|VCUE TextDocument 屬性|  
|說明檔|*\<空白 >*|  
  
 您在精靈的這個頁面設定的值會傳回給屬性頁容器呼叫時，如果**IPropertyPage::GetPageInfo**。 會發生什麼情況的字串之後，這是相依於容器，但通常用來向使用者識別頁面。 標題通常會在您的頁面上方的索引標籤中，文件字串可能會顯示在狀態列上或工具提示 （雖然標準屬性框架完全不使用這個字串）。  
  
> [!NOTE]
>  您在此處設定的字串會儲存為您的專案中的字串資源，由精靈。 您可以輕鬆地編輯這些字串時，如果您需要變更這項資訊之後已產生您的網頁的程式碼使用資源編輯器。  
  
 按一下**確定**，使精靈可產生屬性頁。  
  
##  <a name="vcconediting_the_dialog_resource"></a>編輯對話方塊資源  
 已產生內容頁，您還需要將幾個控制項加入對話方塊資源代表您的頁面。 加入編輯方塊、 靜態文字控制項，並核取方塊，並設定它們的 Id，如下所示：  
  
 ![編輯對話方塊資源](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")  
  
 這些控制項將會用來顯示文件和其唯讀狀態的檔案名稱。  
  
> [!NOTE]
>  對話方塊資源不包含框架或命令的按鈕，也沒有您可能預期的索引標籤的外觀。 這些功能會提供如藉由呼叫所建立的屬性頁面外框[OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437)。  
  
##  <a name="vcconadding_message_handlers"></a>加入訊息處理常式  
 使用就地的控制項，您可以新增任一控制項的值變更時更新中途頁面的狀態訊息處理常式：  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]  
  
 此程式碼可以回應所做變更的編輯控制項或核取方塊，藉由呼叫[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)，通知頁面已變更的網頁站台。 透過啟用或停用頁面站台將回應通常**套用**屬性頁面框架上的按鈕。  
  
> [!NOTE]
>  在您自己的屬性頁，您可能需要以追蹤精確的屬性已被竄改使用者，好讓您可以避免更新未變更的屬性。 這個範例實作該程式碼的原始屬性值追蹤並比較值與目前的值從 UI 來套用變更的時候。  
  
##  <a name="vcconhousekeeping"></a>維護  
 現在，加入幾個`#import`DocProperties.h 陳述式，讓編譯器知道**文件**介面：  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]  
  
 您還需要參閱`IPropertyPageImpl`基底類別，新增下列`typedef`至**CDocProperties**類別：  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a>覆寫 IPropertyPageImpl::SetObjects  
 第一個`IPropertyPageImpl`需要覆寫的方法是[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)。 這裡您將新增程式碼會檢查已傳遞單一物件，它支援**文件**您預期的介面：  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  要對這個頁面支援單一物件，因為您要允許使用者設定物件的檔案名稱，只有一個檔案可以存在的任何位置。  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a>覆寫 IPropertyPageImpl::Activate  
 下一個步驟是先建立頁面時初始化基礎物件的屬性值的屬性頁面。  
  
 在此情況下您應該將下列成員加入至類別，您將也的初始屬性值進行比較時使用頁面的使用者套用變更，因為：  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]  
  
 基底類別實作[Activate](../atl/reference/ipropertypageimpl-class.md#activate)方法會負責建立對話方塊和其控制項，讓您可以覆寫這個方法，並加入您自己的初始設定，在呼叫基底類別：  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]  
  
 此程式碼會使用的 COM 方法**文件**介面，以取得您感興趣的屬性。 然後它會使用所提供的 Win32 應用程式開發介面包裝函式[CDialogImpl](../atl/reference/cdialogimpl-class.md)和其基底類別，以向使用者顯示的屬性值。  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a>覆寫 IPropertyPageImpl::Apply  
 當使用者想要將其變更套用至物件時，會呼叫屬性頁站台[套用](../atl/reference/ipropertypageimpl-class.md#apply)方法。 這是要進行中的程式碼相反的動作的地方**Activate** — 而**Activate**採用物件中的值，以及它們發送到 [屬性] 頁面上的控制項**套用**會使用屬性頁上的控制項的值，並將該物件。  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  對於檢查[m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty)這個實作的開頭是為了避免不必要更新的物件，如果初始檢查**套用**呼叫一次以上。 此外，還有針對每個屬性值，以確保僅變更導致的方法呼叫來檢查**文件**。  
  
> [!NOTE]
> **文件**公開**FullName**為唯讀屬性。 若要更新屬性頁所做的變更為基礎的文件的檔案名稱，您必須使用**儲存**方法，以使用不同的名稱儲存檔案。 因此，若要限制本身沒有屬性頁中的程式碼來取得或設定屬性。  
  
##  <a name="vccontesting_the_property_page"></a>顯示屬性頁  
 若要顯示此頁面，您需要建立一個簡單的 helper 物件。 協助程式物件會提供方法，可簡化**OleCreatePropertyFrame**顯示在單一頁面的應用程式開發介面連接至單一物件。 將設計此協助程式，使其可用於從 Visual Basic。  
  
 使用[加入類別對話方塊](../ide/add-class-dialog-box.md)和[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)產生新的類別，並使用`Helper`做為其簡短名稱。 一旦建立之後，加入的方法，如下表所示。  
  
|項目|值|  
|----------|-----------|  
|方法名稱|`ShowPage`|  
|參數|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption`參數是要顯示為對話方塊的標題的標題。 `bstrID`參數是字串，表示為 CLSID 或 ProgID 屬性頁的顯示。 `pUnk`參數將會是`IUnknown`屬性頁將設定其屬性之物件的指標。  
  
 實作的方法，如下所示：  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a>建立巨集  
 一旦您已經建置專案時，您可以測試屬性頁，並使用簡單的巨集，您可以建立並執行 Visual Studio 開發環境中的協助程式物件。 這個巨集將會建立協助程式物件，然後呼叫其**ShowPage**方法使用的 ProgID **DocProperties**屬性頁和**IUnknown**文件的指標目前在 Visual Studio 編輯器中使用。 您需要為這個巨集程式碼如下所示：  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
 
Public Module AtlPages  
 
    Public Sub Test()  
    Dim Helper  
    Helper = CreateObject("ATLPages7.Helper.1")  
 
    On Error Resume Next  
    Helper.ShowPage(_ 
    ActiveDocument.Name,
    _ 
 "ATLPages7Lib.DocumentProperties.1",
    _ 
    DTE.ActiveDocument _)  
    End Sub  
 
End Module  
```  
  
 當您執行這個巨集時，將顯示的檔案名稱和目前現用的文字文件的唯讀狀態顯示屬性頁。 文件的唯讀狀態只會反映寫入在開發環境; 文件的能力它不會影響磁碟上檔案的唯讀屬性。  
  
## <a name="see-also"></a>請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../visual-cpp-samples.md)

