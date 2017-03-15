---
title: "建立 MFC DLL 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], creating projects
- DLLs [C++], MFC
- projects [C++], creating
- DLLs [C++], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: c403d1351c43e043fd3048d342dafcf069951446
ms.lasthandoff: 02/24/2017

---
# <a name="creating-an-mfc-dll-project"></a>建立 MFC DLL 專案
MFC DLL 是二進位檔案，做為多個應用程式可以同時使用的函式的共用程式庫。 建立 MFC DLL 專案的最簡單方式是使用 MFC DLL 精靈。  
  
> [!NOTE]
>  在 IDE 中功能的外觀可能取決於您目前使用的設定或版本，並可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>若要建立 MFC DLL 專案使用 MFC DLL 精靈  
  
1.  請依照下列說明主題中的指示[使用 Visual c + + 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
 **請注意**中**新的專案**對話方塊中，選取`MFC DLL`開啟 MFC DLL 精靈的 [範本] 窗格中的圖示。  
  
1.  定義使用的應用程式設定[應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)頁面[MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
2.  按一下 [**完成**關閉精靈並開啟新專案中的**方案總管] 中**。  
  
 您的專案建立之後，您可以檢視在 [方案總管] 中建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual c + + 專案類型](http://msdn.microsoft.com/library/912b4ba2-7719-43d5-b087-db33e3f9329a)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [部署應用程式](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


