---
title: 說明檔 (WinHelp) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 505506c7f3a14a73c6b0c859a70938fee3eed69e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="help-files-winhelp"></a>說明檔 (WinHelp)
當選取 加入應用程式的說明支援 WinHelp 類型會建立下列檔案**即時線上說明**核取方塊，然後選取  **WinHelp 格式**中[進階功能](../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 應用程式精靈頁面。  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|原始程式檔|說明編譯器用來建立您的程式或控制項的說明檔說明專案檔。|  
|*Projname*.rtf|*Projname*\hlp|說明檔|包含您可以編輯的範本主題以及有關自訂.hpj 檔。|  
|*Projname*.cnt|*Projname*\hlp|說明檔|提供的結構**內容**Windows 說明中的視窗。|  
|Makehelp.bat|*專案名稱*|原始程式檔|用來編譯專案時，建置說明專案系統。|  
|Print.rtf|*Projname*\hlp|說明檔|如果您的專案包含列印支援 （預設值），建立。 描述列印命令和對話方塊。|  
|*.bmp|*Projname*\hlp|資源檔|包含不同產生的說明檔主題的影像。|  
  
 您可以加入 WinHelp 支援 MFC ActiveX 控制項專案選取**產生說明檔**中[應用程式設定](../mfc/reference/application-settings-mfc-activex-control-wizard.md)MFC ActiveX 控制項精靈 索引標籤。 下列檔案會加入至您的專案，當您將加入 MFC ActiveX 控制項的說明支援：  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|原始程式檔|專案檔，說明編譯器用來建立您的程式或控制項的說明檔。|  
|*Projname*.rtf|*Projname*\hlp|專案|包含您可以編輯的範本主題以及有關自訂.hpj 檔。|  
|Makehelp.bat|*專案名稱*|原始程式檔|用來編譯專案時，建置說明專案系統。|  
|Bullet.bmp|*專案名稱*|資源檔|使用標準的說明檔主題來代表項目符號清單。|  
  
## <a name="see-also"></a>另請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)