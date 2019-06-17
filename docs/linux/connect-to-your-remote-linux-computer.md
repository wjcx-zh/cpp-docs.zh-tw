---
title: 在 Visual Studio 中連線至您的遠端 Linux 電腦
description: 如何從 Visual Studio C++ 專案內連線至遠端 Linux 電腦。
ms.date: 06/07/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6348681ecc8e6f7863b2119810db24879526a1c6
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821606"
---
# <a name="connect-to-your-remote-linux-computer"></a>連線到遠端 Linux 電腦

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range="vs-2019"

當適用於 Linux (WSL) Visual Studio 的目標 Windows 子系統直接透過檔案系統與您的 Linux 發行版本互動時，不需要任何遠端連線。

::: moniker-end

針對遠端 Linux 系統 (VM 或實體機器) 建置 C++ Linux 專案時，Linux 程式碼會複製到您的遠端 Linux 電腦，然後根據 Visual Studio 設定編譯。 設定此遠端連線：

1. 第一次建置專案，或選取 [工具] > [選項]  手動建立新項目，並開啟 [跨平台] > [連線管理員]  節點，然後按一下 [新增]  按鈕。

   ![連線管理員](media/settings_connectionmanager.png)

   在任一情況下，都會顯示 [Connect to Remote System]\(連線到遠端系統)  視窗。

   ![連線到遠端系統](media/connect.png)

1. 輸入下列資訊：

   | 進入 | 說明
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 同時支援密碼或私密金鑰
   | **密碼**            | 所輸入使用者名稱的密碼
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **複雜密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

1. 按一下 [連線]  按鈕，嘗試連線到遠端電腦。  如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)