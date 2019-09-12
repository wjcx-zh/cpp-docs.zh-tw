---
title: MFC 加入類別精靈
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908017"
---
# <a name="mfc-add-class-wizard"></a>MFC 加入類別精靈

使用此程式碼 wizard 將類別加入至現有的 MFC 專案，或將類別加入至支援 MFC 的 ATL 專案。 您也可以將 MFC 類別加入至具有 MFC 支援的 Win32 專案。 您在建立專案時所指定的功能會決定此對話方塊中可用的選項。 若要存取嚮導，請在 [[類別嚮導]](mfc-class-wizard.md)中按一下 [**新增類別**]。

![加入 MFC 類別 Wizard](media/add-mfc-class-wizard.png "加入 MFC 類別 Wizard")

## <a name="names"></a>名稱

在此頁面中，指定類別名稱、基類和新類別的檔案名。

- **類別名稱**

  指定新類別的名稱，並針對此頁面上的識別碼和檔案的名稱提供預設的基礎。 C++類別通常會以 "C" 開頭，因此例如，"CMyClass" 會變成 "MyClass"，依此類推。

- **基底類別**

  指定新類別的基類名稱。 根據預設，基類是[CWnd](../../mfc/reference/cwnd-class.md)。 您選取的基底類別會決定此頁面上的其他方塊是否為使用中。

  您設定為基類的類別類型，會決定類別是否有對話方塊識別碼或資源識別碼。 類別的一般類型如下所示：

  - 不需要對話方塊識別碼或資源識別碼的類別，例如[CButton](../../mfc/reference/cbutton-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)或[CDocument](../../mfc/reference/cdocument-class.md)。 這些類別不會使用對話或資源識別碼。 如果您針對基類選取其中一個類別，[**對話方塊識別碼]** 方塊和 [ **DHTML 資源識別碼**] 方塊會呈現灰色。

  - 需要對話方塊識別碼的類別，例如[CDialog](../../mfc/reference/cdialog-class.md)、 [CFormView](../../mfc/reference/cformview-class.md)或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)。

  - 類別[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，其需要對話方塊識別碼、DHTML 資源識別碼和 HTML 檔案名。

  對於需要對話識別碼的類別，您可能會發現使用[資源編輯器](../../windows/resource-editors.md)來建立對話資源、在[類別的 Wizard](mfc-class-wizard.md)中指派其識別碼，然後建立與該資源識別碼相關聯的類別，會更有效率。 如需建立標準 Windows 對話方塊的詳細資訊，請參閱[建立新的對話方塊](../../windows/creating-a-new-dialog-box.md)。

  > [!NOTE]
  > 如果您先建立對話方塊資源，並從`CDHtmlDialog`衍生其新類別，請刪除 [預設] 對話方塊上顯示的標準 Windows **[確定]** 和 [**取消**] 按鈕。 [標準 Windows] 對話方塊會主控 DHTML 表單，其中包含自己的 **[確定] 和 [** **取消**] 按鈕。

  雖然您的對話方塊可以同時包含 Windows 控制項和 DHTML 控制項，但並不建議您這麼做。

- **對話方塊識別碼**

  如果您`CDialog`選取、 `CFormView`、 `CPropertyPage`或`CDHtmlDialog`作為**基類**，則指定對話方塊的識別碼。

- **.h 檔案**

  設定新物件類別的標頭檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，在您按一下精靈中的 [完成] 之前，精靈不會將它儲存至選取的位置。

  精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

  設定新物件類別的實作檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。

  精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **Active accessibility**

  藉由在此函式中呼叫[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) ，啟用 MFC 對 Active Accessibility 的支援。 此選項適用于衍生自[CWnd](../../mfc/reference/cwnd-class.md)的類別。

- **Automation**

  設定[自動化](../../mfc/automation.md)支援的類別層級。 類別層級的自動化適用于所有支援自動化的類別。 它也適用于使用 Automation 支援所建立的專案。 也就是[支援 ATL](../../atl/reference/mfc-support-in-atl-projects.md)的 mfc 專案，或是您在 Mfc 應用程式精靈的 [ [Advanced Features](../../mfc/reference/advanced-features-mfc-application-wizard.md) ] 頁面中選取了 [**自動化**] 核取方塊的 mfc 專案。

   下列基類無法使用自動化支援：

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

## <a name="see-also"></a>另請參閱

[MFC 類別](../../mfc/reference/adding-an-mfc-class.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)
