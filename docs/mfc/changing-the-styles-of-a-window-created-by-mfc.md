---
title: 變更視窗的樣式建立的 MFC |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34ea35bd43e2bf4e96cbc1552ff169789c1068a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>變更 MFC 所建立之視窗的樣式
其版`WinMain`函式，MFC 會為您註冊數個標準的視窗類別。 因為您通常不編輯 MFC 的`WinMain`，該函式給予您沒有機會變更 MFC 預設視窗樣式。 本文說明如何變更現有的應用程式中的這類的預先登錄的視窗類別樣式。  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> 變更在新的 MFC 應用程式中的樣式  
 如果您使用 Visual c + + 2.0 或更新版本，您可以變更預設視窗樣式應用程式精靈 中的，當您建立您的應用程式。 在應用程式精靈的使用者介面功能頁面上，您可以變更您的主框架視窗和 MDI 子視窗的樣式。 其中一個視窗類型，您可以指定框架粗細 （粗或精簡） 和下列任何一項：  
  
-   視窗是否有最小化或最大化的控制項。  
  
-   是否此視窗會顯示一開始最小化、 最大化，或兩者都關閉。  
  
 主框架視窗中，您也可以指定視窗是否具有系統功能表。 對於 MDI 子視窗，您可以指定視窗是否支援分割窗格。  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> 變更現有的應用程式中的樣式  
 如果您要變更現有的應用程式中的視窗屬性，請改為遵循本文的其餘部分中的指示。  
  
 若要變更與應用程式精靈建立的架構應用程式所使用的預設視窗屬性，覆寫視窗的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虛擬成員函式。 `PreCreateWindow` 允許應用程式存取建立程序通常在內部管理[CDocTemplate](../mfc/reference/cdoctemplate-class.md)類別。 這個架構會呼叫`PreCreateWindow`之前建立的視窗。 藉由修改[CREATESTRUCT](../mfc/reference/createstruct-structure.md)結構傳遞至`PreCreateWindow`，您的應用程式可以變更用來建立視窗的屬性。 比方說，若要確保視窗不會使用標題，請使用下列的位元運算：  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../visual-cpp-samples.md)範例應用程式示範這項技術的變更視窗的屬性。 根據您的應用程式中變更`PreCreateWindow`，可能需要呼叫此函式的基底類別實作。  
  
 下列討論涵蓋 SDI 案例和[MDI 案例](#_core_the_mdi_case)。  
  
##  <a name="_core_the_sdi_case"></a> SDI 案例  
 在單一文件介面 (SDI) 應用程式架構的預設視窗樣式是組合**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式。 **FWS_ADDTOTITLE**是指示架構以新增到視窗的標題的文件標題 MFC 特定樣式。 若要變更在 SDI 應用程式視窗的屬性，覆寫`PreCreateWindow`函式，在您的類別衍生自`CFrameWnd`(其中的應用程式精靈名稱`CMainFrame`)。 例如:   
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 此程式碼建立而不需要最小化和最大化 按鈕以及可調整大小框線的主框架視窗。 將視窗一開始是在螢幕上置中。  
  
##  <a name="_core_the_mdi_case"></a> MDI 案例  
 更多工作，才能變更多個文件介面 (MDI) 應用程式中的子視窗的視窗樣式。 根據預設，使用應用程式精靈建立的 MDI 應用程式會使用預設[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)在 MFC 中定義的類別。 若要變更的 MDI 子視窗的視窗樣式，您必須衍生新類別從`CMDIChildWnd`並取代所有參考`CMDIChildWnd`您專案中使用新類別的參考。 最有可能的唯一參考`CMDIChildWnd`應用程式中位於您的應用程式`InitInstance`成員函式。  
  
 在 MDI 應用程式中使用的預設視窗樣式是組合**WS_CHILD**， **WS_OVERLAPPEDWINDOW**，和**FWS_ADDTOTITLE**樣式。 若要變更視窗的 MDI 應用程式的子視窗的屬性，覆寫[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)函式，在您的類別衍生自`CMDIChildWnd`。 例如:   
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 此程式碼會建立不含最大化按鈕的 MDI 子系。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
-   [視窗樣式](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## <a name="see-also"></a>另請參閱  
 [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

