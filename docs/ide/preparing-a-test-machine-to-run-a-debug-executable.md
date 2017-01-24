---
title: "準備測試電腦以執行偵錯可執行檔 | Microsoft Docs"
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
  - "偵錯可執行檔, 準備測試電腦以執行"
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 準備測試電腦以執行偵錯可執行檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要準備電腦以測試用 Visual C\+\+ 所建置之應用程式的偵錯版本，您必須部署該應用程式所依賴之 Visual C\+\+ 程式庫 DLLs 的偵錯版本。  若要找出必須部署哪些 DLLs，請依照[了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)中所列的步驟進行。  Visual C\+\+ 程式庫 DLLs 的偵錯版本通常在名稱最後為「d」字母，例如，msvcr100.dll 的偵錯版本名稱是 msvcr100d.dll。  
  
> [!NOTE]
>  應用程式的偵錯版本無法轉散發，而且各種 Visual C\+\+ 程式庫 DLLs 的偵錯版本也都無法轉散發。  您可以只在其他電腦上部署應用程式的偵錯版本及 Visual C\+\+ DLL，只為了在沒有安裝 Visual Studio 的電腦上偵錯及測試應用程式。  如需詳細資訊，請參閱[轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
 有三種方法可以一起部署 Visual C\+\+ 程式庫 DLLs 的偵錯版本和應用程式的偵錯版本：  
  
-   使用包含應用程式正確的程式庫版本和結構的合併模組之安裝專案，以使用集中部署安裝特定 Visual C\+\+ DLL 的偵錯版本至 %windir% \\ system32 \\ 目錄。  合併模組會在 \\ Common Files \\ Merge Modules \\ 中的 Program Files 或 Program Files \(x86\) 目錄中被找到。  合併模組的偵錯版本在 namefor 範例 \( Microsoft\_VC110\_DebugCRT\_x86.msm\) 中進行偵錯。  您可以在 [逐步解說：使用安裝專案部署 Visual C\+\+ 應用程式](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中找到這種部署的範例。  
  
-   藉由 \\ Microsoft Visual Studio \<版本\>\\ VC \\ redist \\ Debug\_NonRedist \\ 中的 Program Files 或 Program Files Files \(x86\) 目錄所提供的檔案，使用本機部署安裝特定 Visual C\+\+ DLL 的偵錯版本在應用程式的安裝目錄中。  
  
    > [!NOTE]
    >  使用另一部電腦上的 Visual C\+\+ 2005 或 Visual C\+\+ 2008 針對應用程式建置的遠端偵錯，您必須部署 Visual C\+\+ 程式庫 DLL 的偵錯版本做為共用並存組件。  您可以使用安裝專案或 Windows Installer 安裝對應的合併模組。  
  
-   使用 Visual Studio 的 \[**組態管理員**\] 對話方塊中的 \[**部署**\] 選項將專案輸出和其他檔案複製至遠端電腦。  您可以在 [為 Visual Studio 專案設定遠端偵錯](../Topic/Set%20Up%20Remote%20Debugging%20for%20a%20Visual%20Studio%20Project.md)中找到這種部署的範例。  
  
 安裝 Visual C\+\+ DLLs 之後，您就可以從網路共用執行遠端偵錯工具。  如需遠端偵錯的詳細資訊，請參閱 [在裝置上設定遠端工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
## 請參閱  
 [在裝置上設定遠端工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Visual C\+\+ 中的部署](../ide/deployment-in-visual-cpp.md)   
 [Windows Installer 命令列選項](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [部署範例](../ide/deployment-examples.md)