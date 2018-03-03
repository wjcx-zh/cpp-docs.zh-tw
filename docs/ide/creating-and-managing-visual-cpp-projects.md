---
title: "建立和管理 Visual c + + 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vcprojects
- creatingmanagingVC
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c38f4c75a41de8b2f2b494941c6a52b1ff46fa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>建立和管理 MSBuild 為基礎的 Visual c + + 專案
MSBuild 是 Visual c + + 原生的建置系統，和通常是最佳的建置系統，以用於 UWP 應用程式，以及使用 MFC 或 ATL 程式庫的桌面應用程式使用。 MSBuild 會與 Visual Studio IDE 和專案系統緊密整合，但您也可以使用它從命令列。 從 Visual Studio 2017 開始，Visual c + + 支援[CMake 和其他非 MSBuild 系統，透過開啟資料夾功能](non-msbuild-projects.md)。

MSBuild 專案具有以 XML 格式 (.vcxproj)，指定所有檔案和資源所都需編譯程式，以及其他組態設定，例如目標平台 （x86、 x64 或 ARM），以及您要建置的專案檔案發行版本或偵錯版本的程式。 專案 (一個或多個) 包含在 *「方案」*(solution) 中；例如，方案可能包含數個 Win32 DLL 專案，以及使用這些 DLL 的一個 Win32 主控台應用程式。 當您建置專案時，MSBuild 引擎會使用專案檔，並產生可執行檔及 (或) 您已指定的其他任何自訂輸出。

您可以建立 Visual c + + 專案，選擇**檔案 &#124;新 &#124;專案**，確定已在左窗格中，選取 Visual c + +，，然後選擇 從中間窗格中的專案範本的清單。 當您按一下範本時，在許多情況下將會顯示精靈，可讓您建立專案之前設定各種不同的專案屬性。 您可以檢視並修改這些屬性稍後使用專案屬性頁 (**專案 &#124;屬性**)。  
  
 您也可以建立新專案的：  
  
-   選擇**檔案 &#124;新 &#124;從現有程式碼專案**並遵循提示來加入現有的原始程式碼檔案。 這個選項最適合用於相對較小且簡單的專案，可能是很少或沒有複雜相依性的 25 個或更少原始程式碼檔。  
  
-   從 Makefile 開始，並選擇 [一般] 索引標籤下的 [Makefile 專案] 範本。  
  
-   建立空專案 (下**一般**] 索引標籤) 手動加入 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選擇 [原始程式檔**新增 &#124;現有項目**。  
  
-   using the [Win32 Application Wizard](../windows/win32-application-wizard.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [Visual C++ 專案類型](../ide/visual-cpp-project-types.md)  
 描述 Visual c + + 中可用的 MSBuild 專案類型。  
  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)  
 描述可搭配各種 MSBuild 專案類型的檔案類型。  
  
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 如何使用精靈，搭配 Visual C++ 建立專案。  
  
 [使用專案屬性](../ide/working-with-project-properties.md)  
 描述如何使用屬性頁和屬性工作表，來指定專案設定。  
  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)  
 描述如何將類別、方法、變數及其他項目加入專案，以新增功能。  
  
 [如何：組織組建的專案輸出檔案](../ide/how-to-organize-project-output-files-for-builds.md)  
 描述如何組織專案輸出檔。  
  
## <a name="related-sections"></a>相關章節  
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)  
 提供描述如何從命令列或 Visual Studio 整合式開發環境建置程式等主題的連結。  
  
 [Visual C++ 參考](http://msdn.microsoft.com/en-us/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 提供描述 C 和 C++ 語言參考、Visual C++ 提供的程式庫、Visual C++ 擴充性物件模型以及 Microsoft 巨集組合程式 (MASM) 等主題的連結。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio SDK](http://msdn.microsoft.com/vstudio/extend)
