---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載 | Microsoft Docs
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.custom: ''
ms.date: 07/20/2018
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
ms.openlocfilehash: e33b9ac72ca7691ccbb80a9a30349d3a1e31e194
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207555"
---
# <a name="download-install-and-setup-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

若要在 Linux 上使用 Visual Studio IDE 來建立和偵錯 C++ 專案，您必須安裝**使用 C++ 進行 Linux 開發**工作負載。

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式
1. 啟動 Visual Studio 安裝程式，然後選取 [使用 C++ 進行 Linux 開發] 工作負載。

   ![適用於 Linux 開發的 Visual C++ 延伸模組](media/linuxworkload.png)

2. 按一下 [安裝] 繼續安裝。

## <a name="linux-setup"></a>Linux 安裝程式
目標 Linux 電腦必須已安裝 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，而且 ssh 精靈必須正在執行。  如果還沒有這些項目，您可以如下進行安裝︰
 
1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。  完成後，將會安裝這些服務和工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo service ssh start`
   
   這會啟動服務並在背景中執行，以準備好接受連線。
