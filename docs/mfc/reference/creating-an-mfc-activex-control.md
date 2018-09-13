---
title: 建立 MFC ActiveX 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.project
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0278ce0349b24680252100704031645c995fef51
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535076"
---
# <a name="creating-an-mfc-activex-control"></a>建立 MFC ActiveX 控制項
ActiveX 控制項程式是功能的設計用來讓父應用程式的特定類型的模組化程式。 例如，您可以建立使用按鈕等控制項在對話方塊中或用於在網頁上的工具列中。  

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需詳細資訊，請參閱 < [ActiveX 控制項](../activex-controls.md)。
  
 若要建立 MFC ActiveX 控制項的最簡單方式是使用[MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>若要建立 MFC ActiveX 控制項使用 MFC ActiveX 控制項精靈  
  
1.  請遵循說明主題[使用 Visual C++ 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
2.  在 **新的專案**對話方塊中，選取**MFC ActiveX 控制項**圖示以開啟 MFC ActiveX 控制項精靈的 範本 窗格中。  
  
3.  定義您[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)，[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)，並[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)使用 MFC ActiveX 控制項精靈。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
4.  按一下 **完成**以關閉精靈，並在開發環境中開啟新專案。  
  
 在建立專案之後，您可以檢視中建立的檔案**方案總管 中**。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 在建立專案之後，您可以使用程式碼精靈以新增[函式](../../ide/add-member-function-wizard.md)，[變數](../../ide/add-member-variable-wizard.md)，[事件](../../ide/add-event-wizard.md)，[屬性](../../ide/names-add-property-wizard.md)，及[方法](../../ide/add-method-wizard.md)。 如需有關自訂您的 ActiveX 控制項的詳細資訊，請參閱 < [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   


