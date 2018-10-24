---
title: 在 Visual Studio 中連線至您的遠端 Linux 電腦 | Microsoft Docs
description: 如何從 Visual Studio C++ 專案內連線至遠端 Linux 電腦。
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: bba17549abc9f747d93299cf22c39ae7c3e8f4d6
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601440"
---
# <a name="connect-to-your-remote-linux-computer"></a>連線到遠端 Linux 電腦

在 Visual Studio 中建置 C++ Linux 專案時，Linux 程式碼會複製到您的遠端 Linux 電腦，然後根據 Visual Studio 設定編譯。 設定此遠端連線：

1. 第一次建置專案，或選取 [工具] > [選項] 手動建立新項目，並開啟 [跨平台] > [連線管理員] 節點，然後按一下 [新增] 按鈕。

   ![連線管理員](media/settings_connectionmanager.png)

   在任一情況下，都會顯示 [Connect to Remote System]\(連線到遠端系統) 視窗。
   
   ![連線到遠端系統](media/connect.png)

1. 輸入下列資訊：

   | 進入 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 同時支援密碼或私密金鑰
   | **密碼**            | 所輸入使用者名稱的密碼
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **複雜密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

1. 按一下 [連線] 按鈕，嘗試連線到遠端電腦。  如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)