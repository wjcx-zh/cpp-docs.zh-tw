---
title: 安裝 Visual Studio 中的 c + + 支援 |Microsoft 文件
description: 安裝 Visual c + + 的 Visual Studio 支援
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69092cdd6d79197fb7a2cbdc60b783174b70950b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="install-c-support-in-visual-studio"></a>安裝 Visual Studio 中的 c + + 支援

如果您尚未下載，而且尚未安裝 Visual Studio 和 Visual c + + 工具，以下是如何開始。

## <a name="prerequisites"></a>必要條件

- 寬頻網際網路連線。 Visual Studio 安裝程式可以下載數個 gb 的資料。

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議最佳的開發經驗 Windows 10。 請確定您安裝 Visual Studio 之前，將最新的更新會套用到您的系統。

- 足夠的可用磁碟空間。 Visual Studio 需要至少 7 GB 的磁碟空間，而可能需要 50 GB 或以上如果安裝了許多常用的選項。 我們建議您安裝在您的 c： 磁碟機上。

如需磁碟空間和作業系統需求的詳細資訊，請參閱[Visual Studio 2017 系統需求](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs)。 安裝程式會報告您選取的選項需要多少磁碟空間。

## <a name="installation"></a>安裝

1. 下載最新版 Visual Studio 2017 Windows 安裝程式。

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&utm_source=docs&utm_medium=clickbutton">安裝 Visual Studio 2017 Community</a>

   >[!Tip]
   > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Professional</a> 或 <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Enterprise</a>。

1. 尋找您下載並執行它的安裝程式檔案。 它可能會顯示在瀏覽器中，或您可能會發現您的下載資料夾中。 安裝程式需要系統管理員權限，才能執行。 您可能會看到**使用者帳戶控制**對話方塊要求您授與權限讓安裝程式對您的系統進行變更; 選擇**是**。 如果您有問題，在檔案總管 中尋找下載的檔案，以滑鼠右鍵按一下 安裝程式 圖示，然後選擇**系統管理員身分執行**從內容功能表。

   ![執行安裝程式，Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "執行 Visual Studio 安裝程式")

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 C + + 支援現在是選擇性的工作負載不是預設安裝的一部分。

   ![使用 c + + 桌面開發](../build/media/desktop-development-with-cpp.png "的 c + + 桌面應用程式開發")

    針對 c + + 中，選取**的 c + + 桌面應用程式開發**工作負載，然後選擇 **安裝**。

   ![使用 c + + 工作負載中安裝桌面開發](../build/media/vscpp-concierge-choose-workload.gif "安裝桌面開發搭配 c + + 的工作負載")

1. 當安裝完成時，選擇 **啟動**按鈕來啟動 Visual Studio。

   第一次執行 Visual Studio 中，您必須使用 Microsoft 帳戶登入。 如果您沒有帳戶，您可以免費建立一個。 您也必須選擇的主題。 別擔心，您可以變更它稍後如果您想要。 

   可能需要 Visual Studio 幾分鐘，以準備好使用第一次您執行此程式碼。 以下是什麼樣子螢光快速中：

   ![Visual Studio 2017 登入](../build/media/vscpp-quickstart-first-run.gif "Visual Studio 2017 登入")

   當您再次執行時，visual Studio 會啟動速度。

1. Visual Studio 開啟時，查看在標題列的旗標圖示會反白顯示：

   ![Visual Studio 2017 通知 旗標](../build/media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知 旗標")

   如果會反白顯示，請選取以開啟**通知**視窗。 如果有適用於 Visual Studio 的任何更新，建議您立即安裝。 安裝完成之後，請重新啟動 Visual Studio。

在 Visual Studio 執行時，即準備好繼續進行下一個步驟。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立 c + + 專案](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
