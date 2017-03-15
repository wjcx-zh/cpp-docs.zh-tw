---
title: "Visual C++ 專案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "程式 [C++]，專案"
  - "專案範本 [Visual Studio]，C++"
  - "TODO 註解 [C++]"
  - "專案 [C++]，類型"
  - "範本 [C++]，專案"
  - "應用程式 [C++]，專案"
  - "Visual C++ 專案，類型"
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 專案類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用專案範本，來建立適用於您要建立之專案類型的基本程式結構、功能表、工具列、圖示、參考及 `#include` 陳述式。 Visual Studio 包括各種類型的 Visual C\+\+ 專案範本，並為它們中的許多提供精靈，以便您可以在建立專案時，自訂專案。 在您建立專案之後，您立即就可以對其進行建置，並執行應用程式。在您開發應用程式時，間歇地進行建置是一個很好的做法。  
  
 您無需使用範例來建立專案，但在大部分情況下，使用範本會更有效率，因為與從頭建立專案相比，使用範本可以更輕鬆地修改所提供的專案檔及結構。  
  
> [!NOTE]
>  您可以使用 C\+\+ 專案範本，來建立 C 語言專案。 在所產生的專案中，尋找副檔名為 .cpp 的檔案，並將其變更為 .c。 然後，在專案 \(不適用於方案\) 的 \[專案屬性\] 頁面上，展開 \[組態屬性\]、\[C\/C\+\+\]，然後選取 \[進階\]。 將 \[編譯為\] 設定變更為 \[編譯為 C 程式碼 \(\/TC\)\]。  
  
## 專案範本  
 Visual Studio 支援下列 Visual C\+\+ 專案範本。  
  
### 市集應用程式  
  
||  
|-|  
|[適用於市集應用程式的 C\#、VB 和 C\+\+ 專案範本](http://go.microsoft.com/fwlink/p/?LinkID=262279)|  
  
### ATL  
  
|專案範本|如何建立專案|  
|----------|------------|  
|ATL 專案|[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)|  
  
### CLR  
  
|專案範本|  
|----------|  
|[\(NOTINBUILD\) 類別庫範本 \(C\+\+\)](http://msdn.microsoft.com/zh-tw/0d779bfa-5c5a-4b10-a9d5-a6791764a78f)|  
|[如何：建立 CLR 主控台應用程式](../dotnet/how-to-create-clr-console-applications-cpp-cli.md)|  
|[NOTINBUILD CLR 空專案範本 \(C\+\+\)](http://msdn.microsoft.com/zh-tw/f57c5572-5581-440f-b684-eec646764f08)|  
  
### 一般  
  
|專案範本|如何建立專案|  
|----------|------------|  
|空專案|[建立方案與專案](../Topic/Creating%20Solutions%20and%20Projects.md)|  
|自訂精靈|[建立自訂精靈](../ide/creating-a-custom-wizard.md)|  
|Makefile 專案|[建立 Makefile 專案](../ide/creating-a-makefile-project.md)|  
  
### MFC  
  
|專案範本|如何建立專案|  
|----------|------------|  
|MFC ActiveX 控制項|[建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)|  
|MFC 應用程式|[建立 MFC 應用程式](../mfc/reference/creating-an-mfc-application.md)|  
|MFC DLL|[建立 MFC DLL 專案](../mfc/reference/creating-an-mfc-dll-project.md)|  
  
### 測試  
  
|專案範本|如何建立專案|  
|----------|------------|  
|Managed 測試專案|[建立單元測試專案](../Topic/Create%20a%20unit%20test%20project.md)|  
|原生單元測試專案|[使用測試總管針對機器碼執行單元測試](http://msdn.microsoft.com/zh-tw/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
  
### Win32  
  
|專案範本|如何建立專案|  
|----------|------------|  
|Win32 主控台專案|[建立主控台應用程式](../windows/creating-a-console-application.md)|  
|Win32 專案|[如何：建立 Windows 傳統型應用程式](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)|  
  
## TODO 註解  
 專案範本產生的許多檔案都包含 TODO 註解，以協助您識別您可以提供自己原始程式碼的位置。 如需如何加入程式碼的詳細資訊，請參閱 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md) 和 [Working with Resource Files](../mfc/working-with-resource-files.md)。  
  
## 請參閱  
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用專案建立應用程式](http://msdn.microsoft.com/zh-tw/3339fa90-bac2-4b95-8361-662a2e0e7dfe)   
 [CLR 專案](../ide/files-created-for-clr-projects.md)