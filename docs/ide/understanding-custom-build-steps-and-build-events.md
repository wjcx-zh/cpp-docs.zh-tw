---
title: "了解自訂建置步驟和建置事件 | Microsoft Docs"
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
  - "建置事件 [C++], 事件順序與建置步驟"
  - "建置步驟 [C++]"
  - "建置步驟 [C++], 建置事件"
  - "組建 [C++], 自訂建置步驟"
  - "組建 [C++], 事件"
  - "自訂建置步驟 [C++]"
  - "自訂建置步驟 [C++], 自訂組建"
  - "事件 [C++], 組建"
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 了解自訂建置步驟和建置事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三種從 Visual C\+\+ 開發環境內部自訂建置流程的基本方式：  
  
 **自訂建置步驟**  
 自訂建置步驟就是與專案相關聯的建置規則。  自訂建置步驟可以指定要執行的命令列、任何其他輸入或輸出檔，以及要顯示的訊息。  如需詳細資訊，請參閱[如何：將自訂建置步驟加入至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)。  
  
 **自訂建置工具**  
 自訂建置工具是與一個或多個檔案相關的建置規則。  自訂建置步驟可以將輸入檔案傳遞到自訂建置工具，而產生一個或多個輸出檔案。  例如，MFC 應用程式中的說明檔就是以自訂建置工具建置的。  如需詳細資訊，請參閱[如何：將自訂建置工具加入至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)與[指定自訂建置工具](../ide/specifying-custom-build-tools.md)。  
  
 **建置事件**  
 建置事件可以讓您自訂專案的建置。  有三種建置事件：「*建置前*」\(Pre\-build\)、「*連結前*」\(Pre\-link\) 和「*建置後*」\(Post\-build\)。  建置事件可以讓您指定某項動作於建置程序中的指定時間發生。  例如，您可以使用建置事件在專案完成建置之後以 **regsvr32.exe** 登錄某個檔案。  如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。  
  
 [疑難排解組建自訂](../ide/troubleshooting-build-customizations.md)可以協助您確保您的自訂建置步驟和建置事件都能順利執行。  
  
 自訂建置步驟或建置事件的輸出格式，也可以增進工具的可用性。  如需詳細資訊，請參閱[格式化自訂建置步驟或建置事件的輸出](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)。  
  
 建置事件和自訂建置步驟會配合其他建置步驟以下列順序執行：  
  
1.  建置前事件  
  
2.  個別檔案上的自訂建置工具  
  
3.  MIDL  
  
4.  資源編譯器  
  
5.  C\/C\+\+ 編譯器  
  
6.  連結前事件  
  
7.  連結器 \(Linker\) 或管理員 \(如果適合的話\)  
  
8.  資訊清單工具  
  
9. BSCMake  
  
10. 專案上的自訂建置步驟  
  
11. 建置後事件  
  
 `custom build step on the project` 和 `post-build event` 會再其他所有建置程序完成後循序執行。  
  
## 請參閱  
 [在 Visual Studio 中建置 C\+\+ 專案](../ide/building-cpp-projects-in-visual-studio.md)   
 [建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [Tool Build Order Dialog Box](http://msdn.microsoft.com/zh-tw/6204c5b1-7ce9-4948-9ff6-0268642ee14c)