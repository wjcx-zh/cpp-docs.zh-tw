---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載 | Microsoft Docs
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 403f1bcd8634c3f471f34ff1266501de5bf05d52
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601388"
---
# <a name="download-install-and-setup-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

您可以在 Windows 中使用 Visual Studio IDE 來建立、編輯 C++ 專案 (執行於 Linux 實體電腦、虛擬機器或[適用於 Linux 的 Windows 子系統](/windows/wsl/about)) 並為其進行偵錯。 針對上述任何一種情況，請先安裝**使用 C++ 進行 Linux 開發**工作負載。

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋功能表中，鍵入「Visual Studio 安裝程式」，在**應用程式**結果下方找到該安裝程式，並對其按兩下。 安裝程式開啟後，選擇 [修改]，然後按一下 [工作負載]標籤。向下捲動至 [其他工具組]，然後選取 [使用 C++ 進行 Linux 開發] 工作負載。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果您使用 CMake，或您的目標是 IoT 或內嵌平台，請前往右側的 [安裝詳細資料] 窗格，在 [使用 C++ 進行 Linux 開發] 下方展開 [選用元件] 並選擇您需要的元件。 

1. 按一下 [修改] 繼續安裝。


## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上的另一個選項是啟動適用於 Linux 的 Windows 子系統。 如需詳細資訊，請參閱 [Windows 10 安裝指南](/windows/wsl/install-win10)。

## <a name="linux-setup"></a>Linux 安裝程式

目標 Linux 電腦必須已安裝 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，而且 ssh 精靈必須正在執行。 使用本機電腦來自動同步遠端標頭以進行 Intellisense 支援時，需要 **zip**。 如果還沒有這些應用程式，您可以依下列方式進行安裝︰

1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。  完成後，將會安裝這些服務和工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo service ssh start`

   這會啟動服務並在背景中執行，以準備好接受連線。
