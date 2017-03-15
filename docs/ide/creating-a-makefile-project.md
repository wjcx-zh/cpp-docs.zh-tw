---
title: "建立 Makefile 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.makefile.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Makefile 專案, 建立"
  - "專案檔 [C++], Makefile 專案"
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 Makefile 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您是在命令列中使用 Makefile 建置專案，那麼 Visual Studio 開發環境將無法辨認您的專案。  若要使用 [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)]、[!INCLUDE[vsPro](../ide/includes/vspro_md.md)] 或 Visual Studio Express for Windows Desktop 開啟及建置專案，請先選取 MakeFile 專案範本，建立一個空白專案。  然後您就可以使用這個專案在 Visual Studio 開發環境中建置您的專案。  
  
 這個專案在 \[方案總管\] 中不會顯示任何檔案。  這個專案指定的建置設定，會反映在專案的屬性頁中。  
  
 您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。  
  
### 若要建立一個 Makefile 專案  
  
1.  請依照說明主題[使用 Visual C\+\+ 應用程式精靈建立專案](../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[範本\] 窗格中的 \[**Makefile 專案**\] 以開啟精靈。  
  
3.  在[應用程式設定](../ide/application-settings-makefile-project-wizard.md)頁，提供建置、輸出、清除和重建命令的資訊。  
  
4.  按一下 \[**完成**\] 以關閉精靈並在 \[**方案總管**\] 中開啟新建立的專案。  
  
 您可以在屬性頁檢視和編輯專案的屬性。  如需有關顯示屬性頁的資訊，請參閱[設定 Visual C\+\+ 專案屬性](../ide/working-with-project-properties.md)。  
  
## 請參閱  
 [Makefile 專案精靈](../ide/makefile-project-wizard.md)   
 [Makefile 中的特殊字元](../build/special-characters-in-a-makefile.md)   
 [Makefile 內容](../build/contents-of-a-makefile.md)