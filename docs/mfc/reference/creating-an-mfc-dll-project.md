---
title: 建立 MFC DLL 專案
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6a1718e1f347be46b2f228479d3dbd30027b3160
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077449"
---
# <a name="creating-an-mfc-dll-project"></a>建立 MFC DLL 專案

MFC DLL 是一個二進位檔案，可做為多個應用程式可以同時使用之函式的共用程式庫。 建立 MFC DLL 專案最簡單的方式是使用 MFC DLL Wizard。

> [!NOTE]
>  IDE 中的功能外觀可能取決於您的使用中設定或版本，而且可能與 [說明] 中所描述的不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>使用 MFC DLL Wizard 建立 MFC DLL 專案

1. 遵循說明主題[建立 MFC 應用程式](creating-an-mfc-application.md)中的指示，但從可用的範本清單中選擇 [ **Mfc 動態連結程式庫**] 或 [ **mfc DLL** ]。

1. 使用[MFC DLL Wizard](../../mfc/reference/mfc-dll-wizard.md)的 [[應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)] 頁面定義您的應用程式設定。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按一下 **[完成**] 以關閉嚮導，並在**方案總管**中開啟您的新專案。

專案一旦建立完成之後，即可檢視在 [方案總管] 內建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++ 專案類型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)
