---
title: MFC 加入類別精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: fa9b947ae6fc0e48aaecde61e35a5f4152c85f27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304089"
---
# <a name="mfc-add-class-wizard"></a>MFC 加入類別精靈

使用此程式碼精靈，將類別新增至現有的 MFC 專案，或將類別加入支援 MFC 的 ATL 專案。 您也可以將 MFC 類別加入 MFC 支援的 Win32 專案中。 建立您的專案時指定的功能會判斷在這個對話方塊中可用的選項。

## <a name="names"></a>名稱

在此頁面上，指定類別名稱、 基底類別和新類別的檔案名稱。

- **類別名稱**

  指定新的類別名稱，並提供預設值為基礎的識別碼和在此頁面上的檔案名稱。 C + + 類別通常會開始"C"，比方說，「 CMyClass 」 變成 「 MyClass.h"，依此類推。

- **基底類別**

  指定基底類別的新類別的名稱。 根據預設，基底類別是[CWnd](../../mfc/reference/cwnd-class.md)。 您選取的基底類別判斷是否使用此頁面上的其他方塊。

  您將設為基底類別可讓您判斷類別是否有對話 ID 或資源識別碼。 類別的型別 一般類型的類別如下所示：

  - 這類類別[CButton](../../mfc/reference/cbutton-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，或[CDocument](../../mfc/reference/cdocument-class.md)，這不需要對話識別碼或資源識別碼。 這些類別不使用對話方塊或資源的識別碼。 如果您選取其中一個類別的基底類別，**對話方塊 ID**  方塊中， **DHTML 資源識別碼**方塊會呈暗灰色。

  - 這類類別[CDialog](../../mfc/reference/cdialog-class.md)， [CFormView](../../mfc/reference/cformview-class.md)，或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)，而這需要一個對話的識別碼。

  - 此類別[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，這需要對話方塊 ID、 DHTML 資源識別碼和 HTML 檔案名稱。

  對於需要對話方塊 ID 的類別，您可能會發現它使用更有效率[資源編輯器](../../windows/resource-editors.md)若要建立對話方塊資源，將在其識別碼指派[屬性 視窗](/visualstudio/ide/reference/properties-window)，然後再建立關聯的類別與該資源識別碼。 請參閱[建立新的對話方塊](../../windows/creating-a-new-dialog-box.md)如需有關建立標準的 [Windows] 對話方塊。

  > [!NOTE]
  > 如果您第一次建立對話方塊資源，並衍生其新的類別，從`CDHtmlDialog`，刪除標準 Windows **[確定]** 並**取消**出現在 [預設] 對話方塊的按鈕。 標準的 [Windows] 對話方塊中裝載 DHTML 表單，其中包含它自己 **[確定]** 並**取消**按鈕。

  雖然 Windows 控制項和 DHTML 控制項，可以包含您的對話方塊中，不建議。

- **對話方塊 ID**

  如果您選取指定的對話方塊中，識別碼`CDialog`， `CFormView`， `CPropertyPage`，或`CDHtmlDialog`作為**基底類別**。

- **.h 檔案**

  設定新物件類別的標頭檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，在您按一下精靈中的 [完成] 之前，精靈不會將它儲存至選取的位置。

  精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

  設定新物件類別的實作檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。

  精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **作用中的協助工具**

  藉由呼叫讓 MFC 支援的 Active Accessibility [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)建構函式。 從衍生類別，則使用此選項[CWnd](../../mfc/reference/cwnd-class.md)。

- **DHTML 資源識別碼**

  適用於類別衍生自`CDHtmlDialog`只。 指定 DHTML 對話方塊中的資源識別碼。 資源識別碼會出現在專案的.rc 檔，以及 HTML 對話方塊方塊中的檔案名稱的 HTML 一節。 DHTML 識別的資源，由這個識別碼，由裝載的對話方塊中，識別**對話方塊 ID**。

- **.HTM 檔。**

  適用於類別衍生自`CDHtmlDialog`只。 設定 DHTML 對話方塊中的 HTML 檔案的名稱。 根據預設，這個檔案名稱根據類別名稱。 檔案名稱會出現在 [HTML] 區段的專案的.rc 檔，以及 DHTML 對話方塊方塊中的資源識別碼。

- **Automation**

  設定類別層級的支援[自動化](../../mfc/automation.md)。 在類別層級的自動化是適用於所有支援自動化的類別。 它也可供所建立的自動化支援的專案。 也就是其中一個 MFC 專案[支援 ATL](../../atl/reference/mfc-support-in-atl-projects.md)，或您所選取的 MFC 專案**自動化**中的核取方塊[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 頁面應用程式精靈。

  |選項|描述|
  |------------|-----------------|
  |**無**|表示類別有任何的自動化支援。|
  |**Automation**|指出類別支援自動化。 如果您選取此選項時，新建立的類別可自動化用戶端應用程式，例如 Microsoft Visual Basic 和 Microsoft Excel 的可程式化物件。 此選項不適用於這個表格後面所列的基底類別。|
  |**Creatable 的類型識別碼**|表示在類別和專案支援建立物件，此類別使用自動化的其他應用程式。 使用此選項時，自動化用戶端可以直接建立的 Automation 物件。 在文字方塊中的型別 ID 可由用戶端應用程式來指定要建立; 的物件它是全系統，而且必須是唯一。 此選項不適用於這個表格後面所列的基底類別。|

  自動化支援不適用於下列的基底類別：

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

- **類型識別碼**

  設定類別的型別 ID。 **型別 ID**方塊會串連專案名稱和新的類別名稱，如下所示：*MFCProj.MFCClass*。 此識別碼是您選取時，才可變更**自動化**選項**Creatable 的類型識別碼**。

- **產生 DocTemplate 資源**

  指示應用程式所建立之文件的文件中的範本資源。 若要啟用此核取方塊，專案必須支援 MFC 的文件/檢視架構，而且此類別的基底類別必須[CFormView](../../mfc/reference/cformview-class.md)。

  請參閱[文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

[MFC 類別](../../mfc/reference/adding-an-mfc-class.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)
