---
title: 指定專案設定，從現有程式碼檔案 精靈建立新專案 |Microsoft 文件
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
ms.openlocfilehash: f0f59b802b5a24c1b449f78cccee4744538a5a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定專案設定
您可以使用 [從現有的程式碼檔建立新專案精靈] 的此頁面來指定：  
  
-   新專案的建置環境  
  
-   建置設定，以符合特定類型的新專案以產生  
  
## <a name="task-list"></a>工作清單  
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **使用 Visual Studio**  
 指定要使用 Visual Studio 中會包含用來建置新專案的建置工具。 預設會選取這個選項。  
  
 **專案類型**  
 指定精靈將產生的專案類型。  
  
 **Windows 應用程式專案**  
 表示精靈會產生可執行檔的 Windows 應用程式的專案。 此選項可從**專案類型**下拉式清單方塊。  
  
 **主控台應用程式專案**  
 表示精靈會產生主控台應用程式的專案。 此選項可從**專案類型**下拉式清單方塊。  
  
 **動態連結程式庫 (DLL) 專案**  
 表示精靈會產生空的動態連結程式庫應用程式的專案。 此選項可從**專案類型**下拉式清單方塊。  
  
 **靜態程式庫 (LIB) 專案**  
 表示精靈會產生靜態程式庫應用程式的專案。 此選項可從**專案類型**下拉式清單方塊。  
  
 **加入 ATL 支援**  
 將 ATL 支援加入至新的專案。  
  
 **加入 MFC 支援**  
 將 MFC 支援加入至新的專案。  
  
 **加入 Common Language Runtime 支援**  
 將 CLR 程式設計支援加入至新的專案。  
  
 **通用語言執行平台**  
 指定新的專案，使其符合 CLR 功能。  
  
 **通用語言執行平台 （舊語法）**  
 指定新的專案，使其符合使用 Managed Extensions 是 CLR 程式設計的語法，在 Visual c + + 2005年之前的 c + + 語法。  
  
 **使用外部建置系統**  
 指定要使用則不包含在 Visual Studio 中建置新專案的建置工具。 選取此選項時，您可以指定建置命令列上**指定偵錯組態設定**和**指定發行組態設定**頁面。  
  
> [!NOTE]
>  當**使用外部建置系統**選項已核取，IDE 不會建立新的專案，所以 /D，/ 我、 /FI、 /AI 或 /FU 選項並不需要編譯。 不過，必須正確設定這些選項讓 IntelliSense 正常運作。  
  
## <a name="see-also"></a>另請參閱  
 [指定偵錯組態設定，從現有程式碼檔案 精靈建立新專案](../ide/specify-debug-configuration-settings.md)   
 [從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)