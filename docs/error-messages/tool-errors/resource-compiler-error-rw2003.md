---
title: 資源編譯器錯誤 RW2003
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: f359c1f71f03ce0d946579776230398fb31d046f
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520604"
---
# <a name="resource-compiler-error-rw2003"></a>資源編譯器錯誤 RW2003

產生錯誤

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. **錯誤： 點陣圖資源檔案不是 3.00 格式**

   使用 Windows 2.x 版格式的點陣圖不能用於 3.x 版資源檔。 必須重新繪製點陣圖，或轉換成 3.x 格式。

1. **錯誤： 舊的 DIB 資源名稱中。透過 SDKPAINT 傳遞它**

   無法與 Windows 3.0 格式相容的裝置獨立點陣圖 (DIB) 中指定的資源。 必須重新繪製點陣圖，或轉換成 3.x 格式。

1. **錯誤： 資源檔的資源名稱不是 3.00 格式**

   圖示或游標在指定的資源使用的格式從舊版的 Windows。 必須重新繪製圖示或游標，或轉換成 3.x 格式。

1. **未知的 DIB 標頭格式**

   點陣圖標頭不是 BITMAPCOREHEADER 或 BITMAPINFOHEADER 結構。

1. **無法初始化符號資訊**

   只能在 Visual c + + 中會發生此錯誤。 可能的原因是您有太多開啟的檔案，或您無法開啟，或寫入資料所需的檔案匯入您的指令碼中的符號的 Visual c + +。 Visual c + + 嘗試在指定的目錄中建立這些檔案**TMP**環境變數或如果未指定，目前的目錄。

1. **無法儲存符號資訊**

   只能在 Visual c + + 中會發生此錯誤。 可能的原因是您有太多開啟的檔案，或您無法關閉，或寫入資料所需的檔案匯入您的指令碼中的符號的 Visual c + +。 嘗試將所指定的目錄中使用這些檔案的 visual c + + **TMP**環境變數或如果未指定，目前的目錄。

1. **點陣圖檔的資源檔不是 2.03 格式**

   點陣圖使用的是 2.03 版之前的格式。 必須使用 3.00 版或更新版本的格式來轉換或重繪點陣圖。

1. **資源太大**

   Windows 3.1 資源不能超過約 65000 個位元組。 如果您的資源，然後您將無法使用 Visual c + + 或命令列的資源編譯器進行編譯。 這項限制不適用於資料指標、圖示、點陣圖或其他檔案型資源。

1. **資源檔不是 3.00 格式**

   資料指標或圖示使用 3.00 版之前的格式。 資源必須轉換或重繪使用格式的 3.00 版或更新版本。

1. **無法開啟暫存檔案**

   資源編譯器/Visual C++ 無法開啟暫存檔。 可能的原因是您沒有目錄的寫入權限，或目錄不存在。 資源編譯器/Visual C++ 嘗試在 **TMP** 環境變數所指定的目錄或目前的目錄 (如果未指定) 中使用這些檔案。