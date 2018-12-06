---
title: 在 Visual Studio 2017 中安裝 c + + 支援
description: 安裝 Visual c + + 的 Visual Studio 支援
ms.custom: mvc
ms.date: 11/19/2018
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: ac8439e1709b6bbce6f32580bafee50c9ff30e3f
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977741"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安裝 c + + 支援

如果您還沒有下載並安裝 Visual Studio 2017 和 Visual c + + 工具，以下是如何開始使用。

## <a name="prerequisites"></a>必要條件

- 寬頻網際網路連線。 Visual Studio 安裝程式可以下載好幾 gb 的資料。

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議的最佳開發體驗的 Windows 10。 請確定您安裝 Visual Studio 之前，將最新的更新會套用到您的系統。

- 足夠的可用磁碟空間。 Visual Studio 至少需要 7 GB 的磁碟空間，而可能需要 50 GB 或更多如果安裝了許多常見的選項。 我們建議您將它安裝在您的 c： 磁碟機。

如需磁碟空間和作業系統需求的詳細資訊，請參閱[Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安裝程式會報告您選取的選項需要多少磁碟空間。

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安裝

若要安裝 Visual Studio 2015，請前往[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 執行安裝程式，並選擇 [自訂安裝]，然後選擇 C++ 元件。 C + + 支援新增至現有的 Visual Studio 2015 安裝，按一下 Windows [開始] 按鈕並鍵入**新增或移除程式**。 從結果清單中開啟的程式，然後尋找 Visual Studio 2015 安裝在已安裝的程式清單中。 連按兩下，然後選擇**修改**，然後選取要安裝的 Visual c + + 元件。

一般來說，即使需要使用 Visual Studio 2015 編譯器，編譯您的程式碼，也都非常建議您使用 Visual Studio 2017。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](../porting/use-native-multi-targeting.md)。

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安裝

1. 下載最新的 Visual Studio 2017 安裝程式的 Windows。

   > [!div class="nextstepaction"]
   > [安裝 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 尋找您已下載並執行它的安裝程式檔案。 它可能會顯示在瀏覽器中，或您可能會發現您的 [下載] 資料夾中。 安裝程式需要系統管理員權限，才能執行。 您可能會看到**使用者帳戶控制**詢問是否要授與權限，讓安裝程式對您的系統進行變更; 選擇的對話方塊**是**。 如果您遇到問題，在檔案總管中尋找下載的檔案，以滑鼠右鍵按一下 [安裝程式] 圖示，然後選擇**系統管理員身分執行**從內容功能表。

   ![下載並安裝 Visual Studio Installer](../build/media/vscpp-concierge-run-installer.gif "下載並安裝 Visual Studio 安裝程式")

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 C + + 的支援現在是選擇性並未預設安裝的工作負載的一部分。

   ![使用 c + + 工作負載的桌面開發](../build/media/desktop-development-with-cpp.png "使用 c + + 的桌面開發")

   C + +，請選取**使用 c + + 的桌面開發**工作負載，然後選擇**安裝**。

   ![安裝包含 c + + 工作負載的桌面開發](../build/media/vscpp-concierge-choose-workload.gif "安裝包含 c + + 工作負載的桌面開發")

1. 當安裝完成時，選擇**啟動**按鈕來啟動 Visual Studio。

   第一次執行 Visual Studio 中，您必須使用 Microsoft 帳戶登入。 如果您沒有帳戶，您可以免費建立一個。 您也必須選擇一個佈景主題。 別擔心，您可以將它變更稍後如果您想要。

   可能需要 Visual Studio 幾分鐘，您就準備好使用您在執行第一次。 以下是看起來像是快速縮時攝影外：

   ![登入的 visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "登入的 Visual Studio 2017")

   當您一次執行時，visual Studio 的啟動速度更快。

1. Visual Studio 開啟時，請查看標題列中的旗標圖示會反白顯示：

   ![Visual Studio 2017 通知 旗標](../build/media/vscpp-first-start-page-flag.png "Visual Studio 2017 的通知旗標")

   如果會反白顯示，請選取它以開啟**通知**視窗。 如果有適用於 Visual Studio 的任何更新，我們建議您立即安裝它們。 安裝完成之後，重新啟動 Visual Studio。

當 Visual Studio 執行時，您已準備好繼續進行下一個步驟。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立 c + + 專案](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
