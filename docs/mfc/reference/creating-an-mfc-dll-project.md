---
title: "建立 MFC DLL 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcdll.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 建立"
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 建立專案"
  - "專案 [C++], 建立"
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 MFC DLL 專案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC DLL 是一種類似於函式共用程式庫的二進位檔案 \(Binary File\)，可讓多個應用程式同時使用。  建立 MFC DLL 專案最簡易的方式是使用 MFC DLL 精靈。  
  
> [!NOTE]
>  IDE 中的功能外觀會依您所使用的設定或版本而定，而且可能與 \[說明\] 中所描述的情形不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用 MFC DLL 精靈建立 MFC DLL 專案  
  
1.  請依照說明主題[使用 Visual C\+\+ 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
 **注意事項：**在 \[**新增專案**\] 對話方塊中，選取 \[範本\] 窗格中的 `MFC DLL` 圖示以開啟 \[MFC DLL 精靈\]。  
  
1.  使用 [MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)的[應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)頁面來定義應用程式設定。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
2.  按一下 \[**完成**\] 關閉精靈，並在 \[**方案總管**\] 中開啟您的新專案。  
  
 一旦建立專案，您就可以在 \[方案總管\] 中檢視建立的檔案。  如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。  如需檔案類型的詳細資訊，請參閱[為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## 請參閱  
 [Visual C\+\+ 專案類型](../Topic/Debugging%20Preparation:%20Visual%20C++%20Project%20Types.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)