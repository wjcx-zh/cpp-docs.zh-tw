---
title: "建立 MFC 應用程式 | Microsoft Docs"
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
  - "應用程式 [MFC]"
  - "MFC [C++], 建立應用程式"
  - "MFC 應用程式"
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 建立 MFC 應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 應用程式以 MFC 程式庫為基礎，是 Windows 的可執行應用程式。  要建立 MFC 應用程式，最簡單的方法就是使用 MFC 應用程式精靈。  
  
> [!IMPORTANT]
>  Visual Studio Express 版本不支援 MFC 專案。  
  
 MFC 可執行檔一般分為五種類型：標準 Windows 應用程式、對話方塊、表單架構應用程式、檔案總管樣式應用程式，以及 Web 瀏覽器樣式應用程式。  如需詳細資訊，請參閱：  
  
-   [使用類別來編寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [建立和顯示對話方塊](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [建立 Web 瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 MFC 應用程式精靈可根據您在精靈中選取的選項，為任意類型的應用程式，產生適當的類別和檔案。  
  
### 若要使用 MFC 應用程式精靈建立 MFC 應用程式  
  
1.  請依照說明主題[使用 Visual C\+\+ 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[範本\] 窗格中的 \[**MFC 應用程式**\] 以開啟精靈。  
  
3.  使用 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)定義應用程式設定。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
4.  按一下 \[完成\] 以關閉精靈，並在開發環境中開啟新專案。  
  
 專案一旦建立完成，即可檢視在**方案總管**內建立的檔案。  如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。  如需檔案類型的詳細資訊，請參閱[為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## 請參閱  
 [Debugging Preparation: Visual C\+\+ Windows Applications](http://msdn.microsoft.com/zh-tw/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)