---
title: 一般屬性（Linux C++專案）
description: 描述您可以在 [一般屬性] 頁面上的 Visual Studio 中設定的 Linux 專案屬性。
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 6d598e9d52037d709cba87d98ad375455d8c00b0
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031343"
---
# <a name="general-properties-linux-c"></a>一般屬性（Linux C++）

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

屬性 | 描述 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑。 它可以包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑。 它可以包含環境變數。
目標名稱 | 指定此專案所產生的檔案名。
目標副檔名 | 指定此專案所產生的副檔名（例如 `.a`）。
清除時要刪除的副檔名 | 以分號分隔的萬用字元規格，用於中繼目錄中要在清除或重建時刪除的檔案。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
平台工具組 | 指定用來建立目前設定的工具組。 如果未設定，則會使用預設工具組。
遠端組建電腦 | 要用於遠端組建、部署和 debug 的目的電腦或裝置。 **Visual Studio 2019 16.1 版**您可以在 [[調試](debugging-linux.md)程式] 頁面上，指定不同的電腦進行調試。
遠端組建根目錄 | 指定遠端電腦或裝置上的目錄路徑。
遠端組建專案目錄 | 指定專案在遠端電腦或裝置上的目錄路徑。
遠端部署目錄 | **Visual Studio 2019 16.1 版**指定要部署專案的遠端電腦或裝置上的目錄路徑。
遠端複製包含目錄 | **Visual Studio 2019 16.5 版** 要以遞迴方式從 Linux 目標複製的目錄清單。 這個屬性會影響 IntelliSense 的遠端標頭複製，而不是組建的。 當**IntelliSense 使用編譯器預設值**設為 false 時，可以使用它。 使用 [C/C++一般] 索引標籤下的 [**其他 include 目錄**]，指定要用於 IntelliSense 和組建的其他 include 目錄。
遠端複製排除目錄 | **Visual Studio 2019 16.5 版***不會*從 Linux 目標複製的目錄清單。 這個屬性通常是用來移除 include 目錄的子目錄。
IntelliSense 使用編譯器預設值 | **Visual Studio 2019 16.5 版**是否要查詢此專案所參考的編譯器，以取得其包含位置的預設清單。 這些位置會自動新增到要複製的遠端目錄清單中。 只有當編譯器不支援類似 gcc 的參數時，才將此屬性設定為 false。 Gcc 和 clang 編譯器都支援 include 目錄的查詢（例如 `g++ -x c++ -E -v -std=c++11`）。
組態類型 | 指定此組態所產生的輸出類型。 | **動態連結程式庫（. so）**<br/>**靜態程式庫（. a）**<br/>**應用程式（out）**<br/>**Makefile**
STL 的使用 | 指定要用於這個組態的 C++ 標準程式庫。 | **共用 GNU 標準 C++ 程式庫**<br/>**靜態 GNU 標準 C++ 程式庫 (-static)**

::: moniker-end
