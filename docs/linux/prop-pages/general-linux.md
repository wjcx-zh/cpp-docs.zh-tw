---
title: 一般屬性 (Linux C++ 專案) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: c17a5e0214e6365d604a80bd4b3891858f0f9186
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626819"
---
# <a name="general-properties-linux-c"></a>一般屬性 (Linux C++)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

屬性 | 描述 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
目標名稱 | 指定這個專案將會產生的檔名。
目標副檔名 | 指定這個專案將會產生的副檔名。 (範例：.a)
清除時要刪除的副檔名 | 清除或重建時中繼目錄中要刪除的檔案。檔案名稱以萬用字元表示，項目之間以分號區隔。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
平台工具組 | 指定用於建置目前組態的工具組；如果未設定，則使用預設工具組。
遠端組建電腦 | 要用於遠端建置、部署及偵錯的目標電腦或裝置。 **Visual Studio 2019 16.1 版**：您可以在 [偵錯](debugging-linux.md) 頁面中指定不同的電腦來進行偵錯。
遠端組建根目錄 | 指定遠端電腦或裝置上的目錄路徑。
遠端組建專案目錄 | 指定專案在遠端電腦或裝置上的目錄路徑。
組態類型 | 指定此組態所產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 (.so)<br>**靜態程式庫 (.a)** - 靜態程式庫 (.a)<br>**應用程式 (.out)** - 應用程式 (.out)<br>**Makefile** - Makefile<br>
STL 的使用 | 指定要用於這個組態的 C++ 標準程式庫。 | **共用 GNU 標準 C++ 程式庫**<br>**靜態 GNU 標準 C++ 程式庫 (-static)**<br>

::: moniker-end
