---
title: 嚴重錯誤 C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488903"
---
# <a name="fatal-error-c1902"></a>嚴重錯誤 C1902

程式資料庫管理員不相符;請檢查您的安裝

程式資料庫檔 (.pdb) 建立使用較新版的 mspdb*XXX*.dll 與您的系統上找到的編譯器。 此錯誤通常表示 mspdbsrv.exe 或 mspdbcore.dll，或其遺漏，或有不同的版本與 mspdb*XXX*.dll。 ( *XXX* mspdb 中的預留位置*XXX*.dll 檔案名稱變更，每個產品版本。 例如，在 Visual Studio 2015 中，檔案名稱是 mspdb140.dll）。

確保相符版本的 mspdbsrv.exe、 mspdbcore.dll 和 mspdb*XXX*.dll 安裝在您的系統上。 請確定版本不相符，尚未複製到目錄，其中包含您的目標平台編譯器和連結工具。 例如，您可能已複製檔案讓您可以叫用的編譯器或連結的工具，從命令提示字元，如果沒有設定**路徑**環境變數據此。