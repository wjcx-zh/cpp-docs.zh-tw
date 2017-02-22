---
title: "Example: Implementing a Property Page | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "屬性頁, 實作"
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Example: Implementing a Property Page
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個範例顯示如何建立會顯示的屬性頁 \(並允許變更\) [文件類別](../mfc/document-classes.md) 介面的屬性。  這個介面是由 Visual Studio 中的資料 [通用環境物件模型範例](../Topic/Common%20Environment%20Object%20Model%20Examples.md) 公開 \(雖然您所建立的屬性頁不在乎物件來操作來源，只要支援正確的介面\)。  
  
 這個範例會根據 [ATLPages 範例](../top/visual-cpp-samples.md)。  
  
 若要完成這個範例，您預期:  
  
-   使用加入類別對話方塊和 ATL 屬性頁精靈的[加入 ATL 屬性頁類別](#vcconusing_the_atl_object_wizard) 。  
  
-   [編輯對話方塊資源](#vcconediting_the_dialog_resource) 將 **文件** 介面的有趣的屬性的新控制項。  
  
-   將屬性頁面網站使用者所做的[將訊息處理常式](#vcconadding_message_handlers) 被告知的變更。  
  
-   加入一些 `#import` 陳述式和一個 typedef 在 [環境維護](#vcconhousekeeping) 部分。  
  
-   驗證物件的[覆寫 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) 傳遞至屬性頁。  
  
-   初始化屬性頁之介面的[覆寫 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) 。  
  
-   更新和最新的屬性值之物件的[覆寫 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) 。  
  
-   [顯示屬性頁](#vccontesting_the_property_page) 會引導您建立簡單的 Helper 物件。  
  
-   將測試屬性頁的[建立巨集](#vcconcreating_a_macro) 。  
  
##  <a name="vcconusing_the_atl_object_wizard"></a> 加入 ATL 屬性頁類別  
 首先，請建立名為 `ATLPages7`DLL 的伺服器上建立新的 ATL 專案。  現在使用 [ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md) 產生屬性頁。  將  屬性頁 **DocProperties** \[**簡短名稱**\] 然後切換至 **字串** 網頁對集合屬性頁指定項目如下表所示。  
  
|項目|值|  
|--------|-------|  
|標題|TextDocument|  
|文件字串|VCUE TextDocument 屬性|  
|Helpfile|*\<blank\>*|  
  
 值在這個精靈頁面的集合中傳回至屬性頁容器，呼叫 **IPropertyPage::GetPageInfo**。  依賴容器，不過，哪些之後發生在字串則通常用來識別網頁的使用者。  標題通常會出現在頁面上的索引標籤，以及文件字串在狀態列或可能會顯示工具提示 \(雖然標準屬性架構完全不會使用這個字串\)。  
  
> [!NOTE]
>  您在此處字串集合儲存在專案中，字串資源是由精靈。  您可以輕鬆編輯這些字串使用資源編輯器，如果需要變更這項資訊，在頁面程式碼產生後。  
  
 按一下  可讓 \[**確定**\] 的精靈會產生屬性頁。  
  
##  <a name="vcconediting_the_dialog_resource"></a> 編輯對話方塊資源  
 現在您的屬性頁會產生之後，您就必須將一些控制項表示網頁的對話方塊資源。  將編輯方塊、靜態文字控制項和一個核取方塊並將其 ID 如下所示:  
  
 ![編輯對話方塊資源](../atl/media/ppgresourcelabeled.png "PPGResourceLabeled")  
  
 這些控制項會用來顯示文件和它的唯讀狀態的檔案名稱。  
  
> [!NOTE]
>  對話方塊資源不包含框架或命令按鈕，也不會有您可能預期的索引標籤的外觀。  這些功能都是由一個屬性頁方塊提供例如呼叫所建立的執行個體 [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437)。  
  
##  <a name="vcconadding_message_handlers"></a> 將訊息處理常式  
 隨著控制項，您可以將訊息處理常式更新網頁的變更狀態時，變更其中一個值:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/CPP/example-implementing-a-property-page_1.h)]  
  
 這個程式碼來回應進行的呼叫加入至編輯控制項或核取方塊變更 [IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)，告知控制網站頁面已變更。  通常頁面網站會透過啟用或停用  屬性頁上方塊中 **套用** 按鈕回應。  
  
> [!NOTE]
>  在您的屬性頁，屬性可由使用者修改的可能需要精確地記錄，好讓您可以避免更新未變更的屬性。  藉由記錄屬性值及其程式碼與 UI 的目前值比較的範例實作，當為時套用變更。  
  
##  <a name="vcconhousekeeping"></a> 環境維護  
 現在加入兩個 `#import` 陳述式加入至 DocProperties.h，讓編譯器知道 **文件** 介面:  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/CPP/example-implementing-a-property-page_2.h)]  
  
 您也將需要參考 `IPropertyPageImpl` 基底類別，將下列 `typedef` 至 **CDocProperties** 類別:  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/CPP/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 覆寫 IPropertyPageImpl::SetObjects  
 您必須覆寫的第一 `IPropertyPageImpl` 方法是 [SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)。  您將加入程式碼來檢查只能有一個傳遞的物件，而且支援您預期的 **文件** 介面:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/CPP/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  因此才會支援這個網頁的單一物件，因為您將允許使用者設定物件的檔案名稱—只有一個檔案可能會在任何一個位置。  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 覆寫 IPropertyPageImpl::Activate  
 當頁面第一次建立時，下一個步驟是使用基礎物件的屬性值的屬性頁。  
  
 此時您應該將下列成員加入到類別，因為您用來比較也會使用初始的屬性值，當使用者在頁面上套用它們的變更時:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/CPP/example-implementing-a-property-page_5.h)]  
  
 [啟動](../Topic/IPropertyPageImpl::Activate.md) 方法的基底類別實作會建立對話方塊和控制項負責，因此，您可以覆寫這個方法與呼叫基底類別 \(Base Class\) 之後將初始化:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/CPP/example-implementing-a-property-page_6.h)]  
  
 這個程式碼會使用 **文件** 介面的 COM 方法取得屬性您所要的。  然後會使用 [CDialogImpl](../atl/reference/cdialogimpl-class.md) 及其基底類別所提供的 Win32 API 包裝函式會顯示屬性值給使用者。  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 覆寫 IPropertyPageImpl::Apply  
 當使用者要將其物件的變更，則屬性頁 [套用](../Topic/IPropertyPageImpl::Apply.md) 網站會呼叫方法。  這是為了讓程式碼的相反的位置在 **啟動** 的\)，而 **啟動** 採用從物件取得值並按下的到屬性頁的控制項， **套用** 接受來自控制項的值在屬性頁並推入至物件。  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/CPP/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  物件的 [m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md) 檢查這個實作的開頭是避免不必要的物件更新的初始檢查 **套用** 是否已多次呼叫。  也會檢查以確保每個的屬性值變更只會使方法呼叫 **文件**。  
  
> [!NOTE]
>  **文件 FullName** 公開為唯讀屬性。  若要更新根據變更的文件的檔名對屬性頁，您必須使用 \[**儲存**\] 方法儲存具有不同名稱的檔案。  因此，  屬性頁上的程式碼不需要自我限制為取得或設定屬性。  
  
##  <a name="vccontesting_the_property_page"></a> 顯示屬性頁  
 若要顯示這個頁面，您必須建立一個簡單的 Helper 物件。  Helper 物件會提供簡化的單一頁面上顯示 **OleCreatePropertyFrame** API 連接至單一物件的方法。  這個 Helper 將所設計，以便從 Visual Basic 使用。  
  
 使用 [加入類別對話方塊。](../ide/add-class-dialog-box.md) 和 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md) 產生新類別和使用 `Helper` 做為簡短名稱。  一旦建立之後，將方法如下表所示。  
  
|項目|值|  
|--------|-------|  
|方法名稱|`ShowPage`|  
|參數|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption` 參數是做為對話方塊的標題的標頭。  `bstrID` 參數是表示 CLSID 或屬性頁的 ProgID 的中顯示的字串。  `pUnk` 參數將會是屬性會由屬性頁設定物件的 `IUnknown` 指標。  
  
 實作方法如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/CPP/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a> 建立巨集  
 一旦建立了專案，您可以測試屬性頁和 Helper 物件使用簡單巨集可以在 Visual Studio 開發環境中建置和執行。  這個巨集就會建立 Helper 物件，然後呼叫其方法 **ShowPage** 使用 **DocProperties** 屬性頁和文件的 **IUnknown** 指標的 ProgID 目前作用中的 Visual Studio 編輯器。  您可以指定這個巨集所需的程式碼如下所示:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
  
Public Module AtlPages  
  
    Public Sub Test()  
        Dim Helper  
        Helper = CreateObject("ATLPages7.Helper.1")  
  
        On Error Resume Next  
        Helper.ShowPage( _  
            ActiveDocument.Name, _  
            "ATLPages7Lib.DocumentProperties.1", _  
            DTE.ActiveDocument _  
            )  
    End Sub  
  
End Module  
```  
  
 當您執行此巨集，將只會顯示目前使用中的 Word 文件的檔案名稱和唯讀狀態的屬性頁。  文件的唯讀狀態只反映了文件撰寫在開發環境中;它不會影響檔案的唯讀屬性在磁碟上。  
  
## 請參閱  
 [屬性頁](../atl/atl-com-property-pages.md)   
 [ATLPages 範例](../top/visual-cpp-samples.md)