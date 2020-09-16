---
title: 在 Visual Studio 中建立 Linux MSBuild c + + 專案
ms.date: 08/04/2020
description: 在 Visual Studio 中建立新的 MSBuild 型 Linux 專案。
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 559a868ebdea7e3b835a82c31849d0e2fdeaa6c9
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686687"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>在 Visual Studio 中建立 Linux MSBuild c + + 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本有提供 Linux 專案。

::: moniker-end

::: moniker range="vs-2017"

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

針對跨平臺編譯，我們建議使用 CMake。 Visual Studio 2019 提供更完整的 CMake 支援。 如果 CMake 不是一個選項，而且您有現有的 Windows Visual Studio 解決方案，您想要擴充以針對 Linux 進行編譯，您可以將 Visual Studio 的 Linux 專案連同 **共用專案** 專案新增至 windows 方案。 將兩個平臺之間共用的程式碼放在 [共用專案] 專案中，然後從 Windows 和 Linux 專案加入該專案的參考。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 2017 中建立新的 Linux 專案，請遵循下列步驟：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 選取 [Visual C++] > [跨平台] > [Linux]**** 節點，然後選取您要建立的專案類型。 輸入**名稱**和**位置**，然後選擇 [確定]****。

   ![顯示 [新增專案] 對話方塊的螢幕擷取畫面，其中包含選取的 Visual C + + > 跨平臺 > Linux、已呼叫的所有專案類型，以及名稱和位置文字方塊也稱為 out。](media/newproject.png)

   | 專案類型 | 描述 |
   | ------------ | --- |
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，其中含有讓 LED 閃爍的範例程式碼 |
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，其中含有將文字輸出至主控台的範例程式碼 |
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，其中不含任何範例程式碼 |
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 組建系統所建置 Linux 電腦為目標的專案 |

## <a name="next-steps"></a>後續步驟

[設定 MSBuild Linux 專案](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱 [下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

當您在 Visual Studio 中建立適用於 Linux 的新 C++ 專案時，可以選擇建立 Visual Studio 專案或 CMake 專案。 本文描述如何建立 Visual Studio 專案。 一般來說，對於可能包含開放原始碼的程式碼，或您想要針對跨平臺開發進行編譯的新專案，我們建議您搭配 Visual Studio 使用 CMake。 您可以使用 CMake 專案，在 Windows 和 Linux 上建立和偵測相同的專案。 如需詳細資訊，請參閱 [建立及設定 Linux CMake 專案](cmake-linux-project.md)。

如果您有現有的 Windows Visual Studio 解決方案，您想要擴充以針對 Linux 進行編譯，而 CMake 不是一個選項，則您可以將 Visual Studio 的 Linux 專案和 **共用專案** 專案新增至 Windows 方案。 將兩個平臺之間共用的程式碼放在 [共用專案] 專案中，然後從 Windows 和 Linux 專案加入該專案的參考。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 2019 中建立新的 Linux 專案，請遵循下列步驟：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 將 [語言]**** 設定為 [C++]****，並搜尋 "Linux"。 選取要建立的專案類型，然後選擇 [下一步]****。 輸入**名稱**和**位置**，然後選擇 [建立]****。

   ![[新增專案] 對話方塊的螢幕擷取畫面，其中包含在 [搜尋] 文字方塊中輸入的 Linux。](media/newproject-vs2019.png)

   | 專案類型 | 描述 |
   | ------------ | --- |
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，其中含有讓 LED 閃爍的範例程式碼 |
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，其中含有將文字輸出至主控台的範例程式碼 |
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，其中不含任何範例程式碼 |
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 組建系統所建置 Linux 電腦為目標的專案 |

## <a name="next-steps"></a>後續步驟

[設定 Linux MSBuild 專案](configure-a-linux-project.md)

::: moniker-end
