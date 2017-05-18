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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: 79987719614dfa3075f9a9090ca1d97f6546ceb3
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1902"></a>嚴重錯誤 C1902
程式資料庫管理員不相符。請檢查您的安裝  
  
程式資料庫檔 (.pdb) 建立使用較新版的 mspdb*XXX*.dll 與您的系統上找到的編譯器。 此錯誤通常表示 mspdbsrv.exe 或 mspdbcore.dll 遺失或有不同的版本與 mspdb*XXX*.dll。 ( *XXX*預留位置 mspdb*XXX*.dll 檔案名稱變更，每個產品版本。 例如，Visual Studio 2015 中的檔案名稱是 mspdb140.dll）。  
  
請確定版本相符的 mspdbsrv.exe、 mspdbcore.dll 和 mspdb*XXX*.dll 安裝在您的系統上。 請確定版本不相符，尚未複製到目錄，其中包含您的目標平台編譯器和連結的工具。 例如，您可能已複製檔案叫用的編譯器或連結的工具，從命令提示字元，如果沒有設定**路徑**環境變數據此。
