---
title: 從現有的程式碼檔建立新專案精靈、指定專案設定 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a75bb6034c8f4c5a80bb64238c26ea599395ff96
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705606"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定專案設定
使用 [從現有的程式碼檔建立新專案精靈] 的這個頁面來指定：  
  
-   新專案的建置環境  
  
-   組建設定，以符合要產生之新專案的特定類型  
  
## <a name="task-list"></a>工作清單  

[如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
- **使用 Visual Studio**

   指定使用 Visual Studio 隨附的建置工具來建置新的專案。 預設會選取這個選項。  
  
- **專案類型**

   指定精靈會產生的專案類型。  
  
- **Windows 應用程式專案**

   表示精靈會為可執行的 Windows 應用程式產生專案。 此選項位於 [專案類型] 下拉式清單方塊中。  
  
- **主控台應用程式專案**

   表示精靈會為主控台應用程式產生專案。 此選項位於 [專案類型] 下拉式清單方塊中。  
  
- **動態連結程式庫 (DLL) 專案**

   表示精靈會為空白動態連結程式庫應用程式產生專案。 此選項位於 [專案類型] 下拉式清單方塊中。  
  
- **靜態程式庫 (LIB) 專案**

   表示精靈會為靜態程式庫應用程式產生專案。 此選項位於 [專案類型] 下拉式清單方塊中。  
  
- **新增 ATL 的支援**

   將 ATL 支援新增至新專案。  
  
- **新增 MFC 的支援**

   將 MFC 支援新增至新專案。  
  
- **新增 Common Language Runtime 的支援**

   將 CLR 程式設計支援新增至新專案。  
  
- **通用語言執行平台**

   指定新專案與 CLR 功能相容。  
  
- **Common Language Runtime (舊語法)**

   指定新專案與受控 Extensions for C++ 語法相容，這是 Visual C++ 2005 之前的 CLR 程式設計語法。  
  
- **使用外部建置系統**

   指定使用 Visual Studio 未隨附的建置工具來建置新的專案。 選取此選項時，您可以在 [指定偵錯組態設定] 和 [指定發行組態設定] 頁面上指定建置命令行。  
  
   > [!NOTE]
   > 核取 [使用外部建置系統] 選項時，IDE 不會建置新的專案，因此編譯不需要 /D、/I、/FI、/AI 或 /FU 選項。 不過，您必須正確設定這些選項，IntelliSense 才能正常運作。  
  
## <a name="see-also"></a>請參閱  
 [從現有的程式碼檔建立新專案精靈、指定偵錯組態設定](../ide/specify-debug-configuration-settings.md)   
 [從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)