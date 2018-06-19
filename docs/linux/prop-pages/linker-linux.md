---
title: 連結器屬性 (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 9187222d2ced21ece2f183655591c483abc8d500
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333101"
---
# <a name="linker-properties-linux-c"></a>連結器屬性 (Linux C++)

## <a name="general"></a>一般

屬性 | 描述 | 選擇
--- | ---| ---
輸出檔案 | 此選項會覆寫連結器所建立之程式的預設名稱和位置。 (-o)
顯示進度 | 列印連結器進度訊息。
版本 | -version 選項會指示連結器將版本號碼置於可執行檔的標頭中。
啟用詳細資訊輸出 | -verbose 選項會指示連結器輸出詳細訊息以供偵錯之用。
追蹤 | --trace 選項會指示連結器將輸入檔案，輸出為已處理的狀態。
追蹤符號 | 列印出現符號的檔案清單。 (--trace-symbol=symbol)
列印地圖 | --print-map 選項會指示連結器輸出連結地圖。
回報未解析的符號參考 | 啟用此選項時，會回報未解析的符號參考。
最佳化記憶體的使用 | 視需要重新讀取符號表，最佳化記憶體的使用。
共用程式庫搜尋路徑 | 允許使用者填入共用程式庫搜尋路徑。 (-rpath-link=path)
其他程式庫目錄 | 允許使用者覆寫環境程式庫路徑。 (-L folder)。
連結器 | 指定在連結期間要叫用的程式，或遠端系統上連結器的路徑。
連結逾時 | 遠端連結逾時 (毫秒)。
複製輸出 | 指定是否要從遠端系統，將組建輸出檔案複製到本機電腦。

## <a name="input"></a>輸入

屬性 | 描述 | 選擇
--- | ---| ---
忽略特定的預設程式庫 | 指定要忽略的一或多個預設程式庫名稱。 (--exclude-libs lib,lib)
忽略預設程式庫 | 忽略預設程式庫，而只搜尋明確指定的程式庫。
強制取消定義符號參考 | 強制在輸出檔案中將符號輸入為未定義的符號。 (-u symbol --undefined=symbol)
程式庫相依性 | 此選項可指定要新增至連結器命令列的其他程式庫。 其他程式庫會新增至連結器命令列的結尾，以 'lib' 作為開頭且以 '.a' 副檔名結尾。  (-lFILE)
其他相依性 | 指定要新增至連結命令列的其他項目。

## <a name="debugging"></a>偵錯

屬性 | 描述 | 選擇
--- | ---| ---
偵錯工具符號資訊 | 來自輸出檔中的偵錯工具符號資訊。 | **包含全部**<br>**僅省略偵錯工具符號資訊**<br>**省略所有符號資訊**<br>
對應檔案名稱 | Map 選項會指示連結器以使用者指定的名稱來建立對應檔案。 (-Map=)

## <a name="advanced"></a>進階

屬性 | 描述 | 選擇
--- | ---| ---
重新配置之後將變數標記為唯讀 | 此選項會在重新配置之後，將變數標記為唯讀。
啟用立即函式繫結 | 此選項會將物件標記為要立即進行函式繫結。
不需要可執行檔堆疊 | 此選項會將輸出標記為不需要可執行檔堆疊。
Whole Archive | Whole Archive 會使用來自來源及其他相依性的所有程式碼。
