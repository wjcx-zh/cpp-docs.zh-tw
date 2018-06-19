---
title: 資源編譯器錯誤 RW2003 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10cbd42d976566b1bd8388b8a42429cd7e57639d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323507"
---
# <a name="resource-compiler-error-rw2003"></a>資源編譯器錯誤 RW2003
產生的錯誤  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  **錯誤： 點陣圖資源檔案不是 3.00 格式**  
  
     使用 Windows 2.x 版格式的點陣圖不能用於 3.x 版資源檔。 必須重繪點陣圖，或轉換成 3.x 格式。  
  
2.  **錯誤： 舊的 DIB 在資源名稱。透過 SDKPAINT 傳遞它**  
  
     無法與 Windows 3.0 格式相容裝置獨立點陣圖 (DIB) 中指定的資源。 必須重繪點陣圖，或轉換成 3.x 格式。  
  
3.  **錯誤： 資源檔的資源名稱不是 3.00 格式**  
  
     圖示或游標置於指定的資源使用的格式從舊版的 Windows。 必須重繪或轉換成 3.x 格式圖示或游標。  
  
4.  **未知的 DIB 標頭格式**  
  
     點陣圖標頭不 BITMAPCOREHEADER 或 BITMAPINFOHEADER 結構。  
  
5.  **無法初始化符號資訊**  
  
     只能在 Visual c + + 中，會發生這個錯誤。 可能的原因是有太多開啟的檔案，否則您無法開啟或寫入資料檔案所需的 Visual c + + 符號匯入您的指令碼。 Visual c + + 嘗試在所指定的目錄中建立這些檔案**TMP**環境變數或如果未指定目前的目錄。  
  
6.  **無法儲存符號資訊**  
  
     只能在 Visual c + + 中，會發生這個錯誤。 可能的原因是有太多開啟的檔案，否則您無法關閉，或寫入資料檔案所需的 Visual c + + 符號匯入您的指令碼。 Visual c + + 會嘗試使用指定的目錄中的檔案**TMP**環境變數或如果未指定目前的目錄。  
  
7.  **點陣圖檔的資源檔不是 2.03 格式**  
  
     點陣圖使用的是 2.03 版之前的格式。 必須使用 3.00 版或更新版本的格式來轉換或重繪點陣圖。  
  
8.  **資源太大**  
  
     Windows 3.1 資源不能超過約 65000 個位元組。 如果您的資源，然後您將無法使用 Visual c + + 或命令列資源編譯器進行編譯。 這項限制不適用於資料指標、圖示、點陣圖或其他檔案型資源。  
  
9. **資源檔不是 3.00 格式**  
  
     資料指標或圖示使用 3.00 版之前的格式。 資源必須轉換或重繪格式使用 3.00 版或更新版本。  
  
10. **無法開啟暫存檔案**  
  
     資源編譯器/Visual C++ 無法開啟暫存檔。 可能的原因是您沒有寫入權限的目錄或目錄不存在。 資源編譯器/Visual C++ 嘗試在 **TMP** 環境變數所指定的目錄或目前的目錄 (如果未指定) 中使用這些檔案。