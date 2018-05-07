---
title: 建立 Makefile 專案 |Microsoft 文件
ms.custom: ''
ms.date: 02/28/2018
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
ms.openlocfilehash: dc854f96f1c41baf28a5af4ca1f253e47d9a8914
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-makefile-project"></a>建立 Makefile 專案

如果您有您從命令列中使用 makefile 建置的現有原始碼程式碼專案，Visual Studio 開發環境會有數種方式將它轉換成可完整利用 Visual Studio IDE 功能的專案。 本文說明如何使用您現有的 makefile，建置您的程式碼，在 IDE 中的 Visual Studio 中建立一個 Makefile 專案。 或者，您可以使用**從現有程式碼檔建立新專案**精靈來建立原生的 MSBuild 專案，從您的原始程式碼。 如需詳細資訊，請參閱[如何：從現有程式碼建立 C++ 專案](how-to-create-a-cpp-project-from-existing-code.md)。 從 Visual Studio 2017 開始，您也可以使用**開啟資料夾**功能，可以使用數個現有的建置系統，就如同原生的 Visual Studio 專案。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](non-msbuild-projects.md)。

若要使用 Visual Studio 開啟並使用您現有的 makefile，建置您的原始程式碼，您先建立新的專案選取 MakeFile 專案範本。 精靈會協助您指定的命令和使用您的 makefile 的環境。 這個專案然後可用來建置您的程式碼，在 Visual Studio 開發環境中。

根據預設，makefile 專案會顯示在 [方案總管] 中的任何檔案。 Makefile 專案指定的建置設定，會反映在專案屬性頁。

您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。 您的 makefile 仍然會控制建置流程，並指定建置目標。

## <a name="to-create-a-makefile-project"></a>若要建立一個 Makefile 專案

1. 請依照下列說明主題中的指示[使用 Visual c + + 應用程式精靈建立專案](../ide/creating-desktop-projects-by-using-application-wizards.md)。

1. 在**新專案**對話方塊方塊中，展開  **Visual c + +** > **一般**，然後選取  **Makefile 專案**中若要開啟專案精靈的 範本 窗格。

1. 在[應用程式設定](../ide/application-settings-makefile-project-wizard.md)頁面上，提供命令，輸出、 清除和重建資訊偵錯及零售組建。

1. 按一下**完成**以關閉精靈並開啟新建立的專案中**方案總管 中**。

您可以在屬性頁檢視和編輯專案的屬性。 請參閱[設定 Visual c + + 專案屬性](../ide/working-with-project-properties.md)如需有關顯示屬性頁資訊。

## <a name="see-also"></a>另請參閱

[Makefile 專案精靈](../ide/makefile-project-wizard.md)<br/>
[Makefile 中的特殊字元](../build/special-characters-in-a-makefile.md)<br/>
[Makefile 內容](../build/contents-of-a-makefile.md)<br/>
