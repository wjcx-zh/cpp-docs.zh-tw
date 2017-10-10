---
title: "嚴重錯誤 C1902 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 89354565f67c8704eee8c8b5f9dcb94523800c63
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1902"></a>嚴重錯誤 C1902
程式資料庫管理員不相符;請檢查您的安裝  
  
程式資料庫 (.pdb) 檔案建立使用較新版的 mspdb*XXX*.dll 比編譯器發現您的系統上。 此錯誤通常表示 mspdbsrv.exe 或 mspdbcore.dll 遺漏，或有不同的版本比 mspdb*XXX*.dll。 ( *XXX* mspdb 中的預留位置*XXX*.dll 檔案名稱變更，每個產品版本。 例如，在 Visual Studio 2015 中，檔案名稱是 mspdb140.dll）。  
  
請確定 mspdbsrv.exe mspdbcore.dll 及 mspdb 的相符版本*XXX*.dll 安裝在您的系統上。 確定版本不相符，尚未複製到包含您的目標平台編譯器和連結工具的目錄。 例如，您可能已複製之檔案叫用的編譯器或連結的工具，從命令提示字元，如果沒有設定**路徑**環境變數據此。
