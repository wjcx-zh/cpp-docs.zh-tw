---
title: "在 Visual Studio 中建置 C++ 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組建 [C++], 關於在 Visual Studio 中建置"
  - "專案 [C++], 建置"
  - "Visual C++ 專案, 建置"
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 Visual Studio 中建置 C++ 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual Studio 整合式開發環境 \(IDE\) 中，有數種方法可以建置整個方案或僅在其中建置一個專案。  您還可以修改建置設定，並指定自訂建置步驟，以讓您的開發處理程序更加有效。  
  
 若要建置在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 開啟且在 \[方案總管\] 中選取的方案，您可以：  
  
-   在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
-   或者，在 \[方案總管\] 中，開啟方案的捷徑功能表，然後選擇 \[建置方案\]。  
  
-   或者，按 F7   \(這是 C\/C\+\+ 開發設定的預設鍵盤捷徑\)。  
  
-   或者，在 \[[命令視窗](../Topic/Command%20Window.md)\] \(在功能表列上，選擇 \[檢視\]、\[其他視窗\]、\[命令視窗\]\) 中，輸入`Build.BuildSolution`。  
  
-   或者，在 \[[快速啟動](../Topic/Quick%20Launch,%20Environment,%20Options%20Dialog%20Box.md)\] 方塊中，輸入 `build build solution`。  
  
 若要建置在 \[方案總管\] 中選取的專案，您可以：  
  
-   在功能表列上，選擇 \[建置\]、\[建置 \<專案名稱\>\]。  
  
-   或者，在 \[方案總管\] 中，開啟專案的捷徑功能表，然後選擇 \[建置\]。  
  
-   或者，在 \[命令視窗\] \(在功能表列上，選擇 \[檢視\]、\[其他視窗\]、\[命令視窗\]\) 中，輸入`Build.BuildOnlyProject`。  
  
-   或者，在 \[快速啟動\] 方塊中，輸入 `build project only build only <project name>`。  
  
 當您在 Visual Studio 中建置 Visual C\+\+ 應用程式時，您可以在專案的 \[屬性頁\] 對話方塊中，修改許多建置設定。  如需如何設定專案屬性的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
 如需如何使用 IDE 來建立建置及偵錯 C\+\+ 專案的範例，請參閱[逐步解說：使用 C\+\+ 探索 Visual Studio IDE](../Topic/Getting%20Started%20with%20C++%20in%20Visual%20Studio.md)。  如需如何使用 IDE 來建置 C\+\+\/CLR 專案的範例，請參閱[逐步解說：編譯針對 Visual Studio 中 CLR 的 C\+\+ 程式](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。  如需如何使用 IDE 來建立 Windows 執行階段應用程式的範例，請參閱[使用 C\+\+ 建立您的第一個 Windows 執行階段應用程式](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx)。  
  
 若要閱讀如何建置、修改建置設定及指定自訂建置步驟的更多資訊，請參閱下列文章。  
  
## 在本節中  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)  
 描述如何在整合式開發環境中自訂建置處理程序。  
  
 [建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)  
 列出您可以在接受字串的位置使用的巨集。  
  
 [建置外部專案](../ide/building-external-projects.md)  
 討論使用整合式開發環境外部功能的建置專案。  
  
 [專案檔](../ide/project-files.md)  
 呈現 .vcxproj 檔案的 XML 結構。  
  
## 相關章節  
 [VC\+\+ Directories, Projects, Options Dialog Box](http://msdn.microsoft.com/zh-tw/e027448b-c811-4c3d-8531-4325ad3f6e02)  
 討論在建置期間，如何修改可執行檔、包含檔、程式庫檔及原始程式碼檔\) 的搜尋路徑  
  
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 提供 Visual Studio 中建置的相關資訊。  
  
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)  
 提供各主題的連結，這些主題用於描述如何從 Visual Studio 的命令列或從其整合式開發環境建置程式。  
  
 [C\/C\+\+ 建置參考](../build/reference/c-cpp-building-reference.md)  
 提供以 C\+\+ 建置程式之概觀、編譯器及連結器選項，以及其他建置工具的連結。  
  
 [從舊版的 Visual C\+\+ 升級專案](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 提供各主題的連結，這些主題涵蓋將 Visual C\+\+ 6.0 \(含\) 以後版本專案升級至 Visual C\+\+ .NET 的問題。  
  
 [Porting and Upgrading Programs](http://msdn.microsoft.com/zh-tw/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)  
 提供移植應用程式的詳細資料，並討論 Makefile。  
  
## 請參閱  
 [Roadmap for Windows Store apps using C\+\+](http://msdn.microsoft.com/zh-tw/0b71e4a4-5d8a-4a20-b2ec-e40062675ec1)