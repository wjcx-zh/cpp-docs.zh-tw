---
title: "建立 MFC ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.activex.project
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e01f0e0c1f24839f1d33184448559c1e8f48ceb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-mfc-activex-control"></a>建立 MFC ActiveX 控制項
ActiveX 控制項程式是功能的設計用來提供特定類型給父應用程式的模組化程式。 例如，您可以建立使用按鈕等控制項在對話方塊中或在網頁中使用的工具列。  
  
 若要建立 MFC ActiveX 控制項的最簡單方式是使用[MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>若要建立 MFC ActiveX 控制項使用 MFC ActiveX 控制項精靈  
  
1.  請依照下列說明主題中的指示[使用 Visual c + + 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新專案**對話方塊中，選取**MFC ActiveX 控制項**圖示以開啟 MFC ActiveX 控制項精靈的 範本 窗格中。  
  
3.  定義您[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)，[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)，和[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)使用 MFC ActiveX 控制項精靈。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
4.  按一下**完成**来關閉精靈並在開發環境中開啟新專案。  
  
 在建立專案之後，您可以檢視中建立的檔案**方案總管 中**。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 在建立專案之後，您可以使用程式碼精靈加入[函式](../../ide/add-member-function-wizard.md)，[變數](../../ide/add-member-variable-wizard.md)，[事件](../../ide/add-event-wizard.md)，[屬性](../../ide/names-add-property-wizard.md)，和[方法](../../ide/add-method-wizard.md)。 如需自訂您的 ActiveX 控制項的詳細資訊，請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [部署應用程式](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

