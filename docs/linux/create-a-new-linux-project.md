---
title: 在 Visual Studio 中建立新 C++ Linux 專案
ms.date: 06/07/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: e39e60c906901420a4809c22b4f4e71d3b621da1
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821652"
---
# <a name="create-a-new-linux-project"></a>建立新的 Linux 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本有提供 Linux 專案。

::: moniker-end

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

當您在 Visual Studio 中建立適用於 Linux 的新 C++ 專案時，可以選擇建立 Visual Studio 專案或 CMake 專案。 本文描述如何建立 Visual Studio 專案。 如需建立 CMake 專案和使用現有 CMake 專案的資訊，請參閱[設定 Linux CMake 專案](cmake-linux-project.md)。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 中建立新的 Linux 專案，請遵循下列步驟：

::: moniker range="vs-2019"

1. 在 Visual Studio 中選取 [檔案] > [新增專案]  ，或按 **Ctrl+Shift+N**。
1. 將 [語言]  設定為 [C++]  ，並搜尋 "Linux"。 選取要建立的專案類型，然後選擇 [下一步]  。 輸入**名稱**和**位置**，然後選擇 [建立]  。

   ![新的 Linux 專案](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. 在 Visual Studio 中選取 [檔案] > [新增專案]  ，或按 **Ctrl+Shift+N**。
1. 選取 [Visual C++] > [跨平台] > [Linux]  節點，然後選取您要建立的專案類型。 輸入**名稱**和**位置**，然後選擇 [確定]  。

   ![新的 Linux 專案](media/newproject.png)

::: moniker-end

   | 專案類型 | 說明 |
   | ------------ | --- |
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，其中含有讓 LED 閃爍的範例程式碼 |
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，其中含有將文字輸出至主控台的範例程式碼 |
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，其中不含任何範例程式碼 |
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 組建系統所建置 Linux 電腦為目標的專案 |

## <a name="next-steps"></a>後續步驟

[設定 Linux 專案](configure-a-linux-project.md)
