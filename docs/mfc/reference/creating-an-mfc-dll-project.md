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
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363953"
---
# <a name="creating-an-mfc-dll-project"></a>建立 MFC DLL 專案

MFC DLL 是一個二進位檔案,充當可由多個應用程式同時使用的函數的共用庫。 創建 MFC DLL 專案的最簡單方法是使用 MFC DLL 嚮導。

> [!NOTE]
> IDE 中功能的外觀可能取決於您的活動設置或版本,並且可能與"説明"中描述的功能不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 有關詳細資訊,請參閱[個人化可視化工作室 IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>使用 MFC DLL 精靈建立 MFC DLL 專案

1. 按照幫助主題[「創建 MFC 應用程式](creating-an-mfc-application.md)」中的說明進行操作,但從可用範本清單中選擇**MFC 動態連結庫**或**MFC DLL。**

1. 使用[MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)[的應用程式設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)頁定義應用程式設定。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按下 **「完成」** 以關閉精靈並在**解決方案資源管理員**中打開新專案。

專案一旦建立完成之後，即可檢視在 [方案總管]**** 內建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++ 專案類型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)
