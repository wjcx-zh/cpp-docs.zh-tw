---
title: 建立 MFC DLL 專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0a5582c81bdc56861a549a2d17cd95ee238975a
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027988"
---
# <a name="creating-an-mfc-dll-project"></a>建立 MFC DLL 專案
MFC DLL 是二進位檔案，做為共用程式庫的多個應用程式可以同時使用的函式。 若要建立 MFC DLL 專案的最簡單方式是使用 MFC DLL 精靈。  
  
> [!NOTE]
>  IDE 功能的外觀可能取決於您目前使用中的設定或版本，且可能與不同說明中所述。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>若要建立 MFC DLL 專案使用 MFC DLL 精靈  
  
1.  請遵循說明主題[使用 Visual C++ 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。  
  
 **附註**中**新增專案**對話方塊中，選取`MFC DLL`圖示以開啟 MFC DLL 精靈的 範本 窗格中。  
  
1.  定義使用的應用程式設定[應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)頁[MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
2.  按一下 [**完成**以關閉精靈，並開啟新的專案中**方案總管] 中**。  
  
 您的專案建立之後，您可以檢視在 [方案總管] 中建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 專案類型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)   
 [使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [部署應用程式](http://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)

