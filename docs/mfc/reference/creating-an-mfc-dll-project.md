---
title: 建立 MFC DLL 專案
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 44671985b2ab22e866a63b284a4b22d87b614667
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446745"
---
# <a name="creating-an-mfc-dll-project"></a>建立 MFC DLL 專案

MFC DLL 是二進位檔案，做為共用程式庫的多個應用程式可以同時使用的函式。 若要建立 MFC DLL 專案的最簡單方式是使用 MFC DLL 精靈。

> [!NOTE]
>  IDE 功能的外觀可能取決於您目前使用中的設定或版本，且可能與不同說明中所述。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>若要建立 MFC DLL 專案使用 MFC DLL 精靈

1. 請依照下列說明主題中的指示[建立C++主控台應用程式專案](../../get-started/tutorial-console-cpp.md)。

**附註**中**新增專案**對話方塊中，選取`MFC DLL`圖示以開啟 MFC DLL 精靈的 範本 窗格中。

1. 定義使用的應用程式設定[應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)頁[MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按一下 [**完成**以關閉精靈，並開啟新的專案中**方案總管] 中**。

您的專案建立之後，您可以檢視中建立的檔案**方案總管 中**。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[視覺效果建立的檔案類型C++專案](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[C++在 Visual Studio 中的專案類型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)

