---
title: "建立 MFC ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.activex.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 建立"
  - "MFC ActiveX 控制項 [C++], 建立"
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 建立 MFC ActiveX 控制項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項程式是一種模組化程式，設計來將特定的功能類型提供給父代 \(Parent\) 應用程式。  例如，您可建立控制項，像是使用在對話方塊的按鈕或是使用在 Web 網頁的工具列。  
  
 建立 MFC ActiveX 控制項最容易的方式是使用 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### 若要使用 MFC ActiveX 控制項精靈建立 MFC ActiveX 控制項  
  
1.  請依照說明主題[使用 Visual C\+\+ 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
2.  在 \[**新增專案**\] 對話方塊中選取 \[範本\] 窗格的 \[MFC ActiveX 控制項\] 圖示，以開啟 MFC ActiveX 控制項精靈。  
  
3.  使用 MFC ActiveX 控制項精靈來定義[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)、[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)和[控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
4.  按一下 \[完成\] 以關閉精靈，並在開發環境中開啟新專案。  
  
 在建立專案之後，您可在**方案總管**中檢視建立的檔案。  如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。  如需檔案類型的詳細資訊，請參閱[為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 在建立專案之後，您可使用程式碼精靈來加入[函式](../../ide/add-member-function-wizard.md)、[變數](../../ide/add-member-variable-wizard.md)、[事件](../../ide/add-event-wizard.md)、[屬性](../../ide/names-add-property-wizard.md)及[方法](../../ide/add-method-wizard.md)。  如需自訂 ActiveX 控制項的詳細資訊，請參閱 [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)