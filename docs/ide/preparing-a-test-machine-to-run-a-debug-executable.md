---
title: "準備測試電腦以執行偵錯的可執行檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 344f413eb2325156996700b6975826600ab997f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>準備測試電腦以執行偵錯可執行檔
若要準備電腦以測試 Visual C++ 所建置之應用程式的偵錯版本，您必須部署該應用程式所依賴之 Visual C++ 程式庫 DLL 的偵錯版本。 若要識別部署的 Dll，請遵循[了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 Visual C++ 程式庫 DLL 的偵錯版本通常在名稱最後為「d」字母，例如，msvcr100.dll 的偵錯版本名稱是 msvcr100d.dll。  
  
> [!NOTE]
>  應用程式的偵錯版本無法轉散發，而且 Visual C++ 程式庫 DLL 的偵錯版本也無法轉散發。 您只能在其他電腦上部署應用程式及 Visual C++ DLL 的偵錯版本，只為了在沒有安裝 Visual Studio 的電腦上偵錯及測試應用程式。 如需詳細資訊，請參閱 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。  
  
 有三種方法可以一起部署 Visual C++ 程式庫 DLL 的偵錯版本和應用程式的偵錯版本：  
  
-   使用包含應用程式正確的程式庫版本和架構的合併模組之安裝專案，以使用集中部署安裝特定 Visual C++ DLL 的偵錯版本至 %windir%\system32\ 目錄。 合併模組位於 Program Files 或 Program Files (x86) 目錄中模組 \common\\。 合併模組的偵錯版本在名稱中有 Debug，例如 Microsoft_VC110_DebugCRT_x86.msm。 此部署的範例，請參閱[逐步解說： 部署 Visual c + + 應用程式所使用之安裝專案](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
-   使用本機部署安裝特定 Visual c + + DLL 的偵錯版本應用程式的安裝目錄中，使用 Program Files 或 Program Files (x86) 目錄位於 \Microsoft Visual Studio 中所提供的檔案\<版本 >\VC\redist\Debug_NonRedist\\。  
  
    > [!NOTE]
    >  對於使用另一部電腦上的 Visual C++ 2005 或 Visual C++ 2008 建置之應用程式的遠端偵錯，您必須部署 Visual C++ 程式庫 DLL 的偵錯版本做為共用並存組件。 您可以使用安裝專案或 Windows Installer 安裝對應的合併模組。  
  
-   使用 the_**部署**選項**Configuration Manager**專案輸出和其他檔案複製到遠端電腦的 Visual Studio 中的對話方塊。 
  
 安裝 Visual C++ DLL 之後，您就可以從網路共用執行遠端偵錯工具。 如需遠端偵錯的詳細資訊，請參閱[遠端偵錯](/visualstudio/debugger/remote-debugging.md)。  
  
## <a name="see-also"></a>請參閱  
 
 [Visual c + + 中的部署](../ide/deployment-in-visual-cpp.md)   
 [Windows Installer 命令列選項](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [部署範例](../ide/deployment-examples.md)[遠端偵錯](/visualstudio/debugger/remote-debugging.md)