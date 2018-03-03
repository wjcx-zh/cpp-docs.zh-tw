---
title: "建立 Makefile 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e86bedbf83cd417cfc41317e5887304cda7ee76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-makefile-project"></a>建立 Makefile 專案
如果您是在命令列中使用 Makefile 建置專案，那麼 Visual Studio 開發環境將無法辨認您的專案。 開啟和建置您的專案使用[!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)]，Visual Studio Professional 或 Visual Studio Express for Windows Desktop，先建立空專案選取 MakeFile 專案範本。 然後您就可以使用這個專案在 Visual Studio 開發環境中建置您的專案。  
  
 這個專案在 [方案總管] 中不會顯示任何檔案。 這個專案指定的建置設定，會反映在專案的屬性頁中。  
  
 您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。  
  
### <a name="to-create-a-makefile-project"></a>若要建立一個 Makefile 專案  
  
1.  請依照下列說明主題中的指示[使用 Visual c + + 應用程式精靈建立專案](../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新專案**對話方塊中，選取**Makefile 專案**開啟精靈的 [範本] 窗格中。  
  
3.  在[應用程式設定](../ide/application-settings-makefile-project-wizard.md)頁面、 提供命令時、 輸出、 清除和重建資訊。  
  
4.  按一下**完成**以關閉精靈並開啟新建立的專案中**方案總管 中**。  
  
 您可以在屬性頁檢視和編輯專案的屬性。 請參閱[設定 Visual c + + 專案屬性](../ide/working-with-project-properties.md)如需有關顯示屬性頁資訊。  
  
## <a name="see-also"></a>請參閱  
 [Makefile 專案精靈](../ide/makefile-project-wizard.md)   
 [Makefile 中的特殊字元](../build/special-characters-in-a-makefile.md)   
 [Makefile 內容](../build/contents-of-a-makefile.md)