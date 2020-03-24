---
title: 嚴重錯誤 C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: 10a411dfc942498a98959d9a23cb42dfb93cf2ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202822"
---
# <a name="fatal-error-c1902"></a>嚴重錯誤 C1902

程式資料庫管理員不相符;請檢查您的安裝

程式資料庫檔案（.pdb）是使用較新版本的 mspdb .dll*XXX*所建立，而不是編譯器在系統上找到的檔案。 此錯誤通常表示 mspdbsrv.exe 或 mspdbcore.dll 遺失，或具有與 mspdb .dll*XXX*不同的版本。 （Mspdb .dll*xxx*.DLL 檔案名中的*xxx*預留位置會隨著每個產品版本而變更。 例如，在 Visual Studio 2015 中，檔案名為 mspdb140）。

請確定您的系統上已安裝 mspdbsrv.exe、mspdbcore.dll 和 mspdb .dll*XXX*的對應版本。 請確定未將不相符的版本複製到包含目標平臺之編譯器和連結工具的目錄。 例如，您可能已複製檔案，因此您可以從命令提示字元叫用編譯器或連結工具，而不需要據此設定**PATH**環境變數。
