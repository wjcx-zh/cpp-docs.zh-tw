---
title: 建立和管理 Visual C++ 專案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b3565893d65990955f0fd28c6cccce7fcb1f32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222239"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>建立和管理以 MSBuild 為基礎的 Visual C++ 專案
MSBuild 是 Visual C++ 的原生建置系統，通常也是最適合用於 UWP 應用程式和使用 MFC 或 ATL 程式庫之桌面應用程式的建置系統。 MSBuild 會與 Visual Studio IDE 和專案系統緊密整合，但您也可以從命令列使用它。 從 Visual Studio 2017 開始，Visual C++ [透過開啟資料夾功能支援 CMake 和其他非 MSBuild 系統](non-msbuild-projects.md)。

以 MSBuild 為基礎的專案包含一個 XML 格式的專案檔 (.vcxproj)，其指定編譯程式所需的所有檔案和資源，並包含其他組態設定，例如目標平台 (x86、x64 或 ARM)，以及您要建置程式的發行版本或偵錯版本。 專案 (一個或多個) 包含在 *「方案」*(solution) 中；例如，方案可能包含數個 Win32 DLL 專案，以及使用這些 DLL 的一個 Win32 主控台應用程式。 當您建置專案時，MSBuild 引擎會使用專案檔，並產生可執行檔及 (或) 您已指定的其他任何自訂輸出。

您可以透過選擇 [檔案] &#124; [新增] &#124; [專案] 來建立 Visual C++ 專案，確定已在左窗格中選取 Visual C++，然後從中間窗格中選擇專案範本的清單。 當您按一下範本時，在許多情況下將會顯示精靈，可讓您在建立專案之前設定各種專案屬性。 您可以稍後使用專案的屬性頁 ([專案] &#124; [屬性]) 來檢視並修改那些屬性。  
  
 您也可以透過  
  
-   選擇 [檔案] &#124; [新增] &#124; [來自現有程式碼的專案]，並遵循提示來新增現有的原始程式碼檔案，以建立新專案。 這個選項最適合用於相對較小且簡單的專案，可能是很少或沒有複雜相依性的 25 個或更少原始程式碼檔。  
  
-   從 Makefile 開始，並選擇 [一般] 索引標籤下的 [Makefile 專案] 範本。  
  
-   建立空專案 (在 [一般] 索引標籤下)，然後以滑鼠右鍵按一下 [方案總管] 中的專案節點，並選擇 [新增] &#124; [現有項目]，以手動新增原始程式碼檔。  
  
-   using the [Win32 Application Wizard](../windows/win32-application-wizard.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [Visual C++ 專案類型](../ide/visual-cpp-project-types.md)  
 描述 Visual C++ 中可用且以 MSBuild 為基礎的專案類型。  
  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)  
 描述與各種 MSBuild 專案類型搭配使用的檔案類型。  
  
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 如何使用精靈，搭配 Visual C++ 建立專案。  
  
 [使用專案屬性](../ide/working-with-project-properties.md)  
 描述如何使用屬性頁和屬性工作表，來指定專案設定。  
  
 [使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)  
 描述如何將類別、方法、變數及其他項目加入專案，以新增功能。  
  
 [如何：組織組建的專案輸出檔案](../ide/how-to-organize-project-output-files-for-builds.md)  
 描述如何組織專案輸出檔。  
  
## <a name="related-sections"></a>相關章節  
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)  
 提供描述如何從命令列或 Visual Studio 整合式開發環境建置程式等主題的連結。  
  
 [Visual C++ 參考](https://msdn.microsoft.com/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 提供描述 C 和 C++ 語言參考、Visual C++ 提供的程式庫、Visual C++ 擴充性物件模型以及 Microsoft 巨集組合程式 (MASM) 等主題的連結。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
