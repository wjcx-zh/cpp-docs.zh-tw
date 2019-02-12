---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.date: 02/06/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: c01c8ddeeb8439a7610c0f6c7c11b608ab3675d8
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763879"
---
# <a name="download-install-and-setup-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

您可以在 Windows 中使用 Visual Studio IDE 來建立、編輯 C++ 專案 (執行於 Linux 實體電腦、虛擬機器或[適用於 Linux 的 Windows 子系統](/windows/wsl/about)) 並為其進行偵錯。 針對上述任何一種情況，請先安裝**使用 C++ 進行 Linux 開發**工作負載。

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋方塊中鍵入「Visual Studio 安裝程式」：![Windows 搜尋方塊](media/visual-studio-installer-search.png)
2. 在 [應用程式] 結果下方尋找該安裝程式，然後按兩下。 安裝程式開啟後，選擇 [修改]，然後按一下 [工作負載]標籤。向下捲動至 [其他工具組]，然後選取 [使用 C++ 進行 Linux 開發] 工作負載。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果您使用 CMake，或您的目標是 IoT 或內嵌平台，請前往右側的 [安裝詳細資料] 窗格，在 [使用 C++ 進行 Linux 開發] 下方展開 [選用元件] 並選擇您需要的元件。

1. 按一下 [修改] 繼續安裝。

## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上的另一個選項是啟動適用於 Linux 的 Windows 子系統。 如需詳細資訊，請參閱 [Windows 10 安裝指南](/windows/wsl/install-win10)。

## <a name="linux-setup-ubuntu"></a>Linux 安裝程式：Ubuntu

目標 Linux 電腦必須已安裝 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，而且 ssh 精靈必須正在執行。 使用本機電腦來自動同步遠端標頭以進行 Intellisense 支援時，需要 **zip**。 如果還沒有這些應用程式，您可以依下列方式進行安裝︰

1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo service ssh start`

   這會啟動服務並在背景執行，以準備好接受連線。

## <a name="linux-setup-fedora"></a>Linux 安裝程式：Fedora

執行 Fedora 的目標電腦使用 **dnf** 套件安裝程式。 若要下載 **openssh-server**、**g++**、**gdb**，**gdbserver** 與 **zip** 並重新啟動 ssh 精靈，請依照下列指示執行：

1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo systemctl start sshd`

   這會啟動服務並在背景執行，以準備好接受連線。

