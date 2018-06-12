---
title: 如何：從現有程式碼建立 C++ 專案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786e5704d7afd07576ab738d907eb841518f8be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330131"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>如何：從現有程式碼建立 C++ 專案

在 Visual Studio 中，您可以使用 [從現有程式碼檔建立新專案精靈] 將現有的程式碼檔案移植到 Visual C++ 專案。 在舊版 Visual Studio 的 Express 版中無法使用此精靈。 此精靈會建立新的解決方案和專案，使用 MSBuild 系統來管理您的原始程式檔和組建組態。  
  
將現有的程式碼檔案移植到 Visual C++ 專案，可讓您使用 IDE 內建的所有原生 MSBuild 專案管理功能。 如果您想要使用現有的建置系統，例如 nmake makefile、CMake 或替代項目，可以改用 [開啟資料夾] 選項。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](../ide/non-msbuild-projects.md)。 這兩個選項都可讓您使用 IDE 功能，例如 [IntelliSense](/visualstudio/ide/using-intellisense) 和[專案屬性](../ide/working-with-project-properties.md)。  
  
### <a name="to-create-a-c-project-from-existing-code"></a>若要從現有程式碼建立 C++ 專案  
  
1.  在 [檔案] 功能表上，指向 [新增]，然後按一下 [現有程式碼中的專案]。  
  
1.  在 [從現有的程式碼檔建立新專案精靈] 的第一頁上，於 [您要建立的專案類型為何] 清單中選取 [Visual C++]。 選擇 [下一步]  繼續進行。 
  
1.  指定專案位置和原始程式檔的目錄。 如需此頁面的詳細資料，請參閱[從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔](../ide/specify-project-location-and-source-files.md)。 選擇 [下一步]  繼續進行。  
  
1.  指定要使用的專案設定。 如需此頁面的詳細資料，請參閱[從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)。 選擇 [下一步]  繼續進行。  

1.  指定要使用的偵錯組態設定。 如需此頁面的詳細資料，請參閱[從現有的程式碼檔建立新專案精靈、指定偵錯組態設定](../ide/specify-debug-configuration-settings.md)。 選擇 [下一步]  繼續進行。  

1.  指定要使用的發行組態設定。 如需此頁面的詳細資料，請參閱[從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)。 選擇 [完成] 產生新專案。  
  
## <a name="see-also"></a>請參閱  

[從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔](../ide/specify-project-location-and-source-files.md)   
[從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[從現有的程式碼檔建立新專案精靈、指定偵錯組態設定](../ide/specify-debug-configuration-settings.md)   
[從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)