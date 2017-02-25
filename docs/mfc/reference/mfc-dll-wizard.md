---
title: "MFC DLL 精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.dll.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL 精靈 [MFC]"
  - "DLL [C++], 建立"
  - "DLL [C++], MFC"
  - "MFC DLL 精靈"
  - "MFC DLL [C++]"
  - "MFC DLL [C++], 建立"
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# MFC DLL 精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在使用 MFC DLL 精靈建立 MFC DLL 專案時，您會取得具有內建功能的工作起始應用程式，能夠在編譯時實作 [DLL](../../build/dlls-in-visual-cpp.md) 的基本功能。  MFC 起始程式包含 C\+\+ 原始程式 \(.cpp\) 檔、資源 \(.rc\) 檔及專案 \(.vcxproj\) 檔。  起始檔案 \(Starter File\) 中所產生的程式碼是以 MFC 為基礎。  如需詳細資訊，請參閱 Visual Studio 為專案產生的 Readme.txt 中的檔案詳細資訊以及 [MFC DLL 精靈產生的類別和函式](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md)。  
  
## 概觀  
 這個精靈畫面描述目前正在建立 [MFC DLL 專案的應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)。  依照預設，專案是建立成為無其他設定的一般 DLL \(MFC 共用\) 專案。  
  
 若要變更這些預設值，請按一下精靈左側欄位中的 \[**應用程式設定**\]，並在 MFC DLL 精靈的畫面中進行變更。  
  
 在您建立 MFC DLL 專案後，可使用 Visual C\+\+ [程式碼精靈](../../ide/adding-functionality-with-code-wizards-cpp.md)在專案中加入物件或控制項。  
  
 您可以在基本 MFC DLL 專案執行下列工作和增強功能類型：  
  
-   [從 DLL 匯出](../../build/exporting-from-a-dll.md)  
  
-   [將可執行檔連結至 DLL](../../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../../build/initializing-a-dll.md)  
  
## 請參閱  
 [建立和管理 Visual C\+\+ 專案](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)   
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [實作介面](../../ide/implementing-an-interface-visual-cpp.md)   
 [其他語言的精靈支援](../../ide/wizard-support-for-other-languages.md)