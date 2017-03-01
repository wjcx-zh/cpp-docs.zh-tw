---
title: "MFC 加入類別精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 08d258c2b8386a4dd0c1d24c6ac6aa10f6c04a63
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-add-class-wizard"></a>MFC 加入類別精靈
使用此程式碼精靈，將類別加入至現有的 MFC 專案，或將類別加入至支援 MFC 的 ATL 專案。 您也可以加入至 Win32 專案 MFC 支援的 MFC 類別。 建立專案時所指定的功能會決定在此對話方塊中可用的選項。  
  
## <a name="names"></a>名稱  
 在此頁面上，指定類別名稱、 基底類別，以及針對新的類別檔案名稱。  
  
 **類別名稱**  
 指定新類別的名稱並提供預設值為基礎的 Id 和在此頁面上的檔案名稱。 C + + 類別通常啟動以"C"，比方說，「 CMyClass 」 變成 「 MyClass.h 」，依此類推。  
  
 **基底類別**  
 指定基底類別的新類別的名稱。 根據預設，基底類別是[CWnd](../../mfc/reference/cwnd-class.md)。 您選取的基底類別會判斷此頁面上的其他方塊是否作用中。  
  
 您設定基底類別判斷類別有對話 ID 或資源識別碼為類別的型別 類別的一般型別如下︰  
  
-   之類的類別[CButton](../../mfc/reference/cbutton-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，或[CDocument](../../mfc/reference/cdocument-class.md)，這不需要對話識別碼或資源識別碼。 這些類別並不會使用對話方塊或資源的識別碼。 如果您選取其中一個類別的基底類別，**對話方塊 ID**方塊和**DHTML 資源識別碼**方塊會呈現暗灰色。  
  
-   之類的類別[CDialog](../../mfc/reference/cdialog-class.md)， [CFormView](../../mfc/reference/cformview-class.md)，或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)，而這需要對話方塊 id。  
  
-   類別[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，皆需要對話方塊 ID、 DHTML 資源識別碼和 HTML 檔案名稱。  
  
 需要對話方塊 ID 的類別，您可能會發現使用更有效率[資源編輯器](../../windows/resource-editors.md)若要建立對話方塊資源，必須將在其 ID[屬性 視窗中](/visualstudio/ide/reference/properties-window)，然後建立該資源 ID 相關聯的類別 請參閱[建立新的對話方塊](../../windows/creating-a-new-dialog-box.md)如需有關建立標準 Windows 對話方塊。  
  
> [!NOTE]
>  如果您先建立對話方塊資源，並衍生其新的類別，從`CDHtmlDialog`，刪除標準 Windows**確定**和**取消**出現在 [預設] 對話方塊的按鈕。 標準 Windows 對話方塊裝載 DHTML 表單，其中包含它自己**確定**和**取消**按鈕。  
  
 雖然 Windows 控制項和 DHTML 控制項，可以包含您的對話方塊，不建議。  
  
 **對話方塊 ID**  
 指定的識別碼 對話方塊中，如果您選取`CDialog`， `CFormView`， `CPropertyPage`，或`CDHtmlDialog`為**基底類別**。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔名稱。 根據預設，這個名稱會根據您在提供的名稱上**類別名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，精靈將不將它儲存到選取的位置直到您按一下**完成**在精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下 **是**附加檔案，按一下 **否**回到精靈，並指定另一個檔案名稱。  
  
 **.cpp 檔**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱會根據您在提供的名稱上**類別名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**在精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下 **是**附加檔案，按一下 **否**回到精靈，並指定另一個檔案名稱。  
  
 **使用中的協助工具**  
 藉由呼叫可讓使用中的協助工具的 MFC 支援[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)建構函式。 此選項可用，類別衍生自[CWnd](../../mfc/reference/cwnd-class.md)。  
  
 **DHTML 資源識別碼**  
 套用至類別衍生自`CDHtmlDialog`只。 指定 DHTML 對話方塊中的資源識別碼。 資源識別碼會出現在 HTML 區段的專案的.rc 檔，以及 HTML 對話方塊 方塊中的檔案名稱。 這個識別碼所識別的 DHTML 資源，由對話方塊中，由**對話方塊 ID**。  
  
 **.HTM 檔。**  
 套用至類別衍生自`CDHtmlDialog`只。 設定 DHTML 對話方塊中的 HTML 檔案的名稱。 根據預設，此檔案名稱根據類別名稱。 檔案名稱會出現在 HTML 區段的專案的.rc 檔，以及 DHTML 對話方塊 方塊中的資源 id。  
  
 **自動化**  
 設定類別層級的支援[自動化](../../mfc/automation.md)。 在類別層級的自動化是適用於所有支援自動化的類別。 它也會提供自動化的支援建立的專案。 也就是其中一個 MFC 專案[支援 ATL](../../atl/reference/mfc-support-in-atl-projects.md)，或在您選取的 MFC 專案**自動化**中核取方塊[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 應用程式精靈頁面。  
  
|選項|描述|  
|------------|-----------------|  
|**無**|指出類別有任何自動化的支援。|  
|**自動化**|表示此類別支援自動化。 如果您選取此選項時，新建立的類別可自動化用戶端應用程式，例如 Microsoft Visual Basic 和 Microsoft Excel 的可程式化物件。 此選項不適用於這個表格後面列出的基底類別。|  
|**建立類型識別碼**|表示類別和專案都支援其他應用程式建立這個類別使用自動化的物件。 使用此選項，自動化用戶端可以直接建立 Automation 物件。 在文字方塊中的型別 ID 用於用戶端應用程式所指定的物件建立;它是全系統，而且必須是唯一。 此選項不適用於這個表格後面列出的基底類別。|  
  
 自動化支援不適用於下列的基底類別︰  
  
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
  
 **類型識別碼**  
 設定類別的型別識別碼。 **類型識別碼**方塊會串連專案名稱和新的類別名稱，如下所示︰ *MFCProj.MFCClass*。 此識別碼是當您選取才可變更**自動化**選項**Creatable 的類型識別碼**。  
  
 **產生 DocTemplate 資源**  
 指示應用程式所建立的文件的文件範本資源。 若要啟用此核取方塊，專案必須支援 MFC 的文件/檢視架構，而且這個類別的基底類別必須是[CFormView](../../mfc/reference/cformview-class.md)。  
  
 請參閱[文件範本和文件/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)

