---
title: "如何： 從現有的程式碼建立 c + + 專案 |Microsoft 文件"
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
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6781709c105c606f6ceb856654525385738c1ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>如何：從現有程式碼建立 C++ 專案

在 Visual Studio 中，您就可以移植您現有的程式碼檔案到 Visual c + + 專案中使用**從現有的程式碼檔建立新專案**精靈。 無法在舊版的 Visual Studio 的 Express 版中使用此精靈。 此精靈會建立新的方案和專案來管理您的原始程式檔和組建組態中使用 MSBuild 系統。  
  
將現有的程式碼檔案移植到 Visual c + + 專案，可讓您使用所有 IDE 內建的原生 MSBuild 專案管理功能。 如果您想要使用現有的建置系統，例如 nmake makefile、 CMake 或替代項目，您可以改用 [開啟資料夾] 選項。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](../ide/non-msbuild-projects.md)。 這兩個選項可讓您使用 IDE 功能，例如[IntelliSense](/visualstudio/ide/using-intellisense)和[專案屬性](../ide/working-with-project-properties.md)。  
  
### <a name="to-create-a-c-project-from-existing-code"></a>若要從現有程式碼建立 C++ 專案  
  
1.  在**檔案**功能表上，指向**新增**，然後按一下 **現有程式碼中的專案**。  
  
1.  第一頁上**從現有程式碼檔建立新專案**精靈中，選取**Visual c + +**中**您要建立的專案類型為何**清單。 選擇 [下一步]  繼續進行。 
  
1.  指定專案位置和原始程式檔的目錄。 如需此頁面上的詳細資訊，請參閱[指定專案位置和原始程式檔，建立新專案從現有程式碼檔精靈](../ide/specify-project-location-and-source-files.md)。 選擇 [下一步]  繼續進行。  
  
1.  指定要使用的專案設定。 如需此頁面上的詳細資訊，請參閱[指定專案設定、 建立新專案從現有程式碼檔精靈](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)。 選擇 [下一步]  繼續進行。  

1.  指定要使用的偵錯組態設定。 如需此頁面上的詳細資訊，請參閱[指定偵錯組態設定、 建立新專案從現有程式碼檔精靈](../ide/specify-debug-configuration-settings.md)。 選擇 [下一步]  繼續進行。  

1.  指定要使用的發行組態設定。 如需此頁面上的詳細資訊，請參閱[指定發行組態設定、 建立新專案從現有程式碼檔精靈](../ide/specify-release-configuration.md)。 選擇**完成**產生新的專案。  
  
## <a name="see-also"></a>請參閱  

[指定專案位置和原始程式檔，請從現有程式碼檔案 精靈建立新專案](../ide/specify-project-location-and-source-files.md)   
[指定專案設定，從現有程式碼檔案 精靈建立新專案](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[指定偵錯組態設定，從現有程式碼檔案 精靈建立新專案](../ide/specify-debug-configuration-settings.md)   
[從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)