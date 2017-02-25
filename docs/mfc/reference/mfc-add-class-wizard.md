---
title: "MFC 加入類別精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 加入類別精靈"
  - "精靈 [MFC]"
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# MFC 加入類別精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用這個程式碼精靈來將類別加入至現有 MFC 專案，或是將類別加入至支援 MFC 的 ATL 專案。  您也可以將 MFC 類別加入至具有 MFC 支援的 Win32 專案。  您在建立專案時指定的功能，將決定這個對話方塊中的可用選項。  
  
## 名稱  
 在這個頁面中指定新類別的類別名稱、基底類別及檔名。  
  
 **類別名稱**  
 指定新類別的名稱，並提供這個頁面上 ID 和檔案名稱的預設基準。  C\+\+ 類別通常會以 "C" 開頭，所以例如 "CMyClass" 就會變成 "MyClass.h"，以此類推。  
  
 **基底類別**  
 指定新類別的基底類別名稱。  根據預設，基底類別是 [CWnd](../../mfc/reference/cwnd-class.md)。  您選取的基底類別將決定這個頁面的其他方塊是否為作用中。  
  
 您設定為基底類別的類別型別，將決定類別是包含對話方塊 ID 或是資源 ID。  類別的一般型別如下：  
  
-   不需要對話方塊 ID 或資源 ID 的類別，例如 [CButton](../../mfc/reference/cbutton-class.md)、[CWnd](../../mfc/reference/cwnd-class.md) 或 [CDocument](../../mfc/reference/cdocument-class.md)。  這些類別並不使用對話方塊或資源 ID。  如果您為基底類別選取以上任一類別，則 \[**對話方塊 ID**\] 方塊和 \[**DHTML 資源 ID**\] 方塊都會停用。  
  
-   需要對話方塊 ID 的類別，例如 [CDialog](../../mfc/reference/cdialog-class.md)、[CFormView](../../mfc/reference/cformview-class.md) 或 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)。  
  
-   需要對話方塊 ID、DHTML 資源 ID 及 HTML 檔名的 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) 類別。  
  
 如果是需要對話方塊 ID 的類別，您可能會發現使用[資源編輯器](../../mfc/resource-editors.md)來建立對話方塊資源，然後在[屬性視窗](../Topic/Properties%20Window.md)中指派其 ID，最後建立與該資源 ID 相關聯的類別，這樣是更有效率的。  如需建立標準 Windows 對話方塊的詳細資訊，請參閱[建立新的對話方塊](../../mfc/creating-a-new-dialog-box.md)。  
  
> [!NOTE]
>  如果您先建立對話方塊資源，然後從 `CDHtmlDialog` 衍生它的新類別，則請刪除出現在預設對話方塊中的標準 Windows \[**確定**\] 和 \[取消\] 按鈕。  標準 Windows 對話方塊會裝載 DHTML 表單，其中包含它本身的 \[**確定**\] 和 \[取消\] 按鈕。  
  
 雖然您的對話方塊可包含 Windows 控制項和 DHTML 控制項，但不建議這樣做。  
  
 **對話方塊 ID**  
 如果您選取 `CDialog`、`CFormView`、`CPropertyPage` 或 `CDHtmlDialog` 做為 \[基底類別\]，請指定對話方塊的 ID。  
  
 **.h 檔案**  
 為新物件類別設定標頭檔 \(Header File\) 的名稱。  依照預設，這個名稱會根據在 \[類別名稱\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置，或將類別宣告附加至現有的檔案。  如果您選擇現有檔案，除非您在精靈中按一下 \[**完成**\]，否則精靈不會將檔案儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別宣告附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **.cpp 檔**  
 為新物件類別設定實作檔 \(Implementation File\) 的名稱。  依照預設，這個名稱會根據在 \[類別名稱\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置。  除非您在精靈中按一下 \[**完成**\]，否則精靈不會將檔案儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別實作 附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **Active Accessibility**  
 藉由在建構函式 \(Constructor\) 中呼叫 [EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md)，啟用 MFC 對 Active Accessibility 的支援。  這個選項可供衍生自 [CWnd](../../mfc/reference/cwnd-class.md) 的類別使用。  
  
 **DHTML 資源 ID**  
 只適用於衍生自 `CDHtmlDialog` 的類別。  指定 DHTML 對話方塊的資源 ID，  資源 ID 和 HTML 對話方塊檔名一起出現在專案 .rc 檔的 HTML 區段，  這個 ID 識別的 DHTML 資源是由 \[對話方塊 ID\] 識別的對話方塊所裝載的。  
  
 **.HTM 檔案**  
 只適用於衍生自 `CDHtmlDialog` 的類別。  為 DHTML 對話方塊設定 HTML 檔案的名稱，  這個檔名依照預設是根據類別名稱來命名，  檔名會和 DHTML 對話方塊資源 ID 一起出現在專案 .rc 檔的 HTML 區段。  
  
 **Automation**  
 設定支援 [Automation](../../mfc/automation.md) 的類別層次。  在類別層次的 Automation 可用於所有支援 Automation 的類別。  它也可以供建立用來支援自動化的專案使用。  也就是說，不是[支援 ATL](../../atl/reference/mfc-support-in-atl-projects.md)的 MFC 專案，就是您在 \[MFC 應用程式精靈\] 的[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)頁面，為其選取 \[**自動化**\] 核取方塊的 MFC 專案。  
  
|選項|說明|  
|--------|--------|  
|**無**|表示類別無 Automation 支援。|  
|**Automation**|表示類別支援 Automation。  如果您選取這個選項，則新建立的類別就可當做可程式化的物件來讓 Automation 用戶端應用程式使用，例如 Microsoft Visual Basic 和 Microsoft Excel。  列在此表之後的基底類別無法使用這個選項。|  
|**可由型別 ID 建立\(E\)**|表示類別和專案支援其他應用程式，而這些應用程式使用 Automation 來建立這個類別的物件。  選取這個選項之後，Automation 用戶端可直接建立 Automation 物件。  用戶端應用程式會使用文字方塊中的型別 ID 來指定要建立的物件；這個 ID 是屬於整個系統的且必須是唯一的。  列在此表之後的基底類別無法使用這個選項。|  
  
 下列基底類別不具 Automation 支援：  
  
-   `CAsyncMonitorFile`  
  
-   `CAsyncSocket`  
  
-   `CCachedDataPathProperty`  
  
-   `CConnectionPoint`  
  
-   `CDatabase`  
  
-   `CDataPathProperty`  
  
-   `CHttpFilter`  
  
-   `CHttpServer`  
  
-   `CInternetSession`  
  
-   `CObject`  
  
-   `CSocket`  
  
 **型別 ID**  
 設定類別的型別 ID。  \[**型別 ID**\] 方塊會串連專案名稱和新類別名稱，如下所示：*MFCProj.MFCClass*。  這個 ID 只有在您選取 \[Automation\] 的 \[可由型別 ID 建立\] 選項時，才可以變更。  
  
 **產生 DocTemplate 資源**  
 指示應用程式建立的文件具有文件樣板資源。  若要啟動這個核取方塊，專案必須支援 MFC 文件\/檢視架構，而這個類別的基底類別必須是 [CFormView](../../mfc/reference/cformview-class.md)。  
  
 如需詳細資訊，請參閱[文件樣板和文件\/檢視建立處理序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 請參閱  
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)