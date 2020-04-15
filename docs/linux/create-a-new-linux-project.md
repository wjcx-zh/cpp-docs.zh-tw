---
title: 在 Visual Studio 中建立新 C++ Linux 專案
ms.date: 10/24/2019
description: 在可視化工作室中創建一個新的基於 MSBuild 的 Linux 專案。
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 1e79dd50756b71aabae7ccec75e57178898e7720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364343"
---
# <a name="create-a-new-linux-project"></a>建立新的 Linux 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本有提供 Linux 專案。

::: moniker-end

::: moniker range="vs-2017"

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

對於跨平台編譯,我們建議使用 CMake。 在 Visual Studio 2019 中,CMake 支援更加完整。 如果 CMake 不是選項,並且您有要擴展為 Linux 編譯的現有 Windows Visual Studio 解決方案,則可以將 Visual Studio Linux 專案以及**共享專案**添加到 Windows 解決方案中。 將共用專案兩個平台之間共用的代碼放在"共用專案"專案中,並從 Windows 和 Linux 專案中添加對該專案的引用。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

要在 Visual Studio 2017 中建立新的 Linux 專案,請按照以下步驟操作:

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 選取 [Visual C++] > [跨平台] > [Linux]**** 節點，然後選取您要建立的專案類型。 輸入**名稱**和**位置**，然後選擇 [確定]****。

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

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 有關詳細資訊,請參閱[下載、安裝和設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

當您在 Visual Studio 中建立適用於 Linux 的新 C++ 專案時，可以選擇建立 Visual Studio 專案或 CMake 專案。 本文描述如何建立 Visual Studio 專案。 通常,對於可能包含開原始程式碼或打算編譯用於跨平臺開發的新專案,我們建議您將 CMake 與 Visual Studio 一起使用。 使用 CMake 專案,您可以在 Windows 和 Linux 上建構和除錯相同的專案。 有關詳細資訊,請參閱[建立與設定 Linux CMake 專案](cmake-linux-project.md)。

如果您有要擴展為 Linux 編譯的現有 Windows Visual Studio 解決方案,並且 CMake 不是選項,則可以將 Visual Studio Linux 專案以及**共用專案**專案添加到 Windows 解決方案中。 將共用專案兩個平台之間共用的代碼放在"共用專案"專案中,並從 Windows 和 Linux 專案中添加對該專案的引用。

## <a name="to-create-a-new-linux-project"></a>建立新的 Linux 專案

要在 Visual Studio 2019 中建立新的 Linux 專案,請按照以下步驟操作:

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 將 [語言]**** 設定為 [C++]****，並搜尋 "Linux"。 選取要建立的專案類型，然後選擇 [下一步]****。 輸入**名稱**和**位置**，然後選擇 [建立]****。

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
