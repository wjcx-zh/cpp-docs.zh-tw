---
title: 在 Visual Studio 中建立新 C++ Linux 專案
ms.date: 10/24/2019
description: 在 Visual Studio 中建立以 MSBuild 為基礎的新 Linux 專案。
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 5d5fa67566d86edb2ed0389fdbe38866b47e2211
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626732"
---
# <a name="create-a-new-linux-project"></a>建立新的 Linux 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本有提供 Linux 專案。

::: moniker-end

::: moniker range="vs-2017"

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

針對跨平臺編譯，建議使用 CMake。 Visual Studio 2019 中的 CMake 支援更完整。 如果 CMake 不是選項，而且您有想要擴充以針對 Linux 編譯的現有 Windows Visual Studio 解決方案，您可以將 Visual Studio Linux 專案新增至 Windows 解決方案，以及**共用專案**專案。 將兩個平臺之間共用的程式碼放在共用專案專案中，並從 Windows 和 Linux 專案加入該專案的參考。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 2017 中建立新的 Linux 專案，請遵循下列步驟：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]，或按 **Ctrl+Shift+N**。
1. 選取 [Visual C++] > [跨平台] > [Linux] 節點，然後選取您要建立的專案類型。 輸入**名稱**和**位置**，然後選擇 [確定]。

   ![新的 Linux 專案](media/newproject.png)

   | 專案類型 | 描述 |
   | ------------ | --- |
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，其中含有讓 LED 閃爍的範例程式碼 |
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，其中含有將文字輸出至主控台的範例程式碼 |
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，其中不含任何範例程式碼 |
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 組建系統所建置 Linux 電腦為目標的專案 |

## <a name="next-steps"></a>後續步驟

[設定 Linux 專案](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝和設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

當您在 Visual Studio 中建立適用於 Linux 的新 C++ 專案時，可以選擇建立 Visual Studio 專案或 CMake 專案。 本文描述如何建立 Visual Studio 專案。 一般來說，對於可能包含開放原始碼或您想要針對跨平臺開發進行編譯的新專案，我們建議您將 CMake 與 Visual Studio 搭配使用。 有了 CMake 專案，您就可以在 Windows 和 Linux 上建立和調試同一個專案。 如需詳細資訊，請參閱[建立和設定 Linux CMake 專案](cmake-linux-project.md)。

如果您有現有的 Windows Visual Studio 解決方案，而您想要擴充以針對 Linux 進行編譯，而 CMake 不是選項，則您可以將 Visual Studio Linux 專案新增至 Windows 解決方案，以及**共用專案**專案。 將兩個平臺之間共用的程式碼放在共用專案專案中，並從 Windows 和 Linux 專案加入該專案的參考。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 2019 中建立新的 Linux 專案，請遵循下列步驟：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]，或按 **Ctrl+Shift+N**。
1. 將 [語言] 設定為 [C++]，並搜尋 "Linux"。 選取要建立的專案類型，然後選擇 [下一步]。 輸入**名稱**和**位置**，然後選擇 [建立]。

   ![新的 Linux 專案](media/newproject-vs2019.png)

   | 專案類型 | 描述 |
   | ------------ | --- |
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，其中含有讓 LED 閃爍的範例程式碼 |
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，其中含有將文字輸出至主控台的範例程式碼 |
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，其中不含任何範例程式碼 |
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 組建系統所建置 Linux 電腦為目標的專案 |

## <a name="next-steps"></a>後續步驟

[設定 Linux 專案](configure-a-linux-project.md)

::: moniker-end
