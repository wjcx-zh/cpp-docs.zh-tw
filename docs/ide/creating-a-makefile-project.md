---
title: 建立 C++ Makefile 專案 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3360d2ed86d220bc59d6f09f582c71b48f7d78c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399479"
---
# <a name="creating-a-c-makefile-project"></a>建立 C++ Makefile 專案

*Makefile* 是文字檔，其中包含如何編譯和連結 (或「建置」) 一組 C++ 原始程式碼檔案的指示。 *Make* 程式會讀取 Makefile 並叫用編譯器、連結器和可能的其他程式來產生可執行檔。 Microsoft 對 *Make* 程式的實作稱為 **NMAKE**。 (根據預設，Visual Studio 使用基於 .vcsproj 檔案的 MSBuild 系統；這是由 [檔案] |[ 新建] | [專案] 所建立。)

如果您有現有的 Makefile 專案，則當您希望在 Visual Studio IDE 中撰寫和/或對其進行偵錯時，可以選擇這些選項：

- 在 Visual Studio 中建立 Makefile 專案，以使用您現有的 Makefile 在 IDE 中建置您的程式碼。 (您將無法使用原生 MSBuild 專案取得所有 IDE 功能。)請參閱下方的[建立 Makefile 專案](#create_a_makefile_project)。
- 使用 [從現有程式碼檔建立新專案精靈]，從您的原始程式碼建立原生 MSBuild 專案。 如需詳細資訊，請參閱[如何：從現有程式碼建立 C++ 專案](how-to-create-a-cpp-project-from-existing-code.md)。
- **Visual Studio 2017 和更新版本**：使用 [開啟資料夾] 功能開啟 Makefile。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](non-msbuild-projects.md)。

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> 使用 Makefile 專案範本建立 Makefile 專案

在 Visual Studio 2017 和更新版本中，已安裝 C++ 桌面開發工作負載時，可以使用 Makefile 專案範本。

遵循精靈來指定 Makefile 所使用的命令和環境。 然後您就可以使用這個專案在 Visual Studio 開發環境中建置您的程式碼。

根據預設，Makefile 專案在 [方案總管] 中不會顯示任何檔案。 Makefile 專案指定的建置設定，會反映在專案的屬性頁中。

您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。 您的 Makefile 仍會控制建置程序並指定建置目標。

1. 在 Visual Studio 起始畫面的 [新增專案] 搜尋方塊中鍵入 "makefile"。 或者，在 [新增專案] 對話方塊中，展開 [Visual C++] > [一般] (Visual Studio 2015) 或 [其他] (Visual Studio 2017，然後選取 [範本] 窗格中的 [Makefile 專案] 以開啟專案精靈。

1. 在 [[應用程式設定]](../ide/application-settings-makefile-project-wizard.md) 頁面中，提供偵錯和零售組建的命令、輸出、清除和重建資訊。

1. 按一下 [完成] 以關閉精靈並在 [方案總管] 中開啟新建立的專案。

您可以在屬性頁檢視和編輯專案的屬性。 如需顯示屬性頁的資訊，請參閱[設定 Visual C++ 專案屬性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>請參閱

[Makefile 專案精靈](../ide/makefile-project-wizard.md)<br/>
[Makefile 中的特殊字元](../build/special-characters-in-a-makefile.md)<br/>
[Makefile 內容](../build/contents-of-a-makefile.md)<br/>
