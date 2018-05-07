---
title: 嚴重錯誤 C1902 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23507b6531f9ee4e5ce5efd5b60a1977206635c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1902"></a>嚴重錯誤 C1902
程式資料庫管理員不相符;請檢查您的安裝  
  
程式資料庫 (.pdb) 檔案建立使用較新版的 mspdb*XXX*.dll 比編譯器發現您的系統上。 此錯誤通常表示 mspdbsrv.exe 或 mspdbcore.dll 遺漏，或有不同的版本比 mspdb*XXX*.dll。 ( *XXX* mspdb 中的預留位置*XXX*.dll 檔案名稱變更，每個產品版本。 例如，在 Visual Studio 2015 中，檔案名稱是 mspdb140.dll）。  
  
請確定 mspdbsrv.exe mspdbcore.dll 及 mspdb 的相符版本*XXX*.dll 安裝在您的系統上。 確定版本不相符，尚未複製到包含您的目標平台編譯器和連結工具的目錄。 例如，您可能已複製之檔案叫用的編譯器或連結的工具，從命令提示字元，如果沒有設定**路徑**環境變數據此。