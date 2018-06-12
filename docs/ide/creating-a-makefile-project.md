---
title: 建立 Makefile 專案 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336774"
---
# <a name="creating-a-makefile-project"></a>建立 Makefile 專案

如果您具有使用 Makefile 從命令列建置的現有原始程式碼專案，Visual Studio 開發環境提供數種方式，將它轉換成可充分利用 Visual Studio IDE 功能的專案。 本文描述如何在 Visual Studio 中建立 Makefile 專案，以使用您現有的 Makefile 在 IDE 中建置您的程式碼。 或者，您可以使用 [從現有程式碼檔建立新專案精靈]，從您的原始程式碼建立原生 MSBuild 專案。 如需詳細資訊，請參閱[如何：從現有程式碼建立 C++ 專案](how-to-create-a-cpp-project-from-existing-code.md)。 從 Visual Studio 2017 開始，您也可以使用 [開啟資料夾] 功能，此功能可使用數個現有的建置系統，就像是原生 Visual Studio 專案一樣。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](non-msbuild-projects.md)。

若要使用 Visual Studio 透過您現有的 Makefile 開啟並建置您的原始程式碼，請先選取 Makefile 專案範本建立新專案。 精靈會協助您指定 Makefile 所使用的命令和環境。 然後您就可以使用這個專案在 Visual Studio 開發環境中建置您的程式碼。

根據預設，Makefile 專案在 [方案總管] 中不會顯示任何檔案。 Makefile 專案指定的建置設定，會反映在專案的屬性頁中。

您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。 您的 Makefile 仍會控制建置程序並指定建置目標。

## <a name="to-create-a-makefile-project"></a>若要建立一個 Makefile 專案

1. 請遵循說明主題[使用 Visual C++ 應用程式精靈建立專案](../ide/creating-desktop-projects-by-using-application-wizards.md)中的指示操作。

1. 在 [新增專案] 對話方塊中，展開 [Visual C++] > [一般]，然後選取 [範本] 窗格中的 [Makefile 專案] 以開啟專案精靈。

1. 在 [[應用程式設定]](../ide/application-settings-makefile-project-wizard.md) 頁面中，提供偵錯和零售組建的命令、輸出、清除和重建資訊。

1. 按一下 [完成] 以關閉精靈並在 [方案總管] 中開啟新建立的專案。

您可以在屬性頁檢視和編輯專案的屬性。 如需顯示屬性頁的資訊，請參閱[設定 Visual C++ 專案屬性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>請參閱

[Makefile 專案精靈](../ide/makefile-project-wizard.md)<br/>
[Makefile 中的特殊字元](../build/special-characters-in-a-makefile.md)<br/>
[Makefile 內容](../build/contents-of-a-makefile.md)<br/>
