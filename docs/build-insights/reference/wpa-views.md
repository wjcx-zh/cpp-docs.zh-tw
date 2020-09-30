---
title: 參考： Windows Performance Analyzer 視圖
description: Windows Performance Analyzer 中提供的 c + + 組建見解視圖參考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a5b13ee08becd472b3bc52319212b84a9c8ffc25
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508803"
---
# <a name="reference-windows-performance-analyzer-views"></a>參考： Windows Performance Analyzer 視圖

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看此版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range="vs-2019"

本文提供 Windows Performance Analyzer (WPA) 中可用之每個 c + + 組建見解視圖的詳細資料。 使用此頁面來尋找：

- 資料行描述;和
- 每個觀點的可用預設值，包括其預定用途和慣用的觀看模式。

如果您不熟悉 WPA，建議您先熟悉 [適用于 c + + Build Insights 的 wpa 基本概念](../tutorials/wpa-basics.md)。

## <a name="build-explorer"></a>Build 總管

Build Explorer 視圖可用來：

- 診斷平行處理問題，
- 判斷您的組建時間是否由剖析、程式碼產生或連結所主導，以及
- 找出瓶頸和異常長的組建活動。

### <a name="build-explorer-view-data-columns"></a>Build Explorer view 資料行

| 資料行名稱 | 描述 |
|-|-|
| BuildTimelineDescription | 文字描述目前活動或屬性發生的時間軸。 |
| BuildTimelineId          | 以零為基底的時間軸識別碼，目前的活動或屬性發生于上。 |
| 元件                | 發出目前事件時正在編譯或連結的元件。 *\<Invocation X Info\>* 當沒有任何元件與這個事件相關聯時，這個資料行的值就是。 X 是在發出事件時所執行之調用的唯一數值識別碼。 此識別碼與這個事件的 InvocationId 資料行中的識別碼相同。 |
| 計數                    | 這個資料列所代表的活動或屬性數目。 此值一律為1，而且只有在將多個資料列分組時，才適用于匯總案例中。 |
| ExclusiveCPUTime         | 此活動使用的 CPU 時間量（以毫秒為單位）。 在子活動中所花費的時間不會包含在此數量中。 |
| ExclusiveDuration        | 活動的毫秒持續時間。 子活動的持續時間不包含在此數量中。 |
| InclusiveCPUTime         | 此活動和所有子活動所使用的 CPU 時間量（以毫秒為單位）。 |
| InclusiveDuration        | 此活動的毫秒持續時間，包括所有子活動。 |
| InvocationDescription    | 發生此事件之調用的文字描述。 描述包括 *cl.exe* 或 *link.exe*，以及唯一的數值調用識別碼。 如果適用，則會包含在叫用期間編譯或連結之元件的完整路徑。 若為未建立任何元件的調用，或建立多個元件的調用，則路徑是空白的。 調用識別碼與 InvocationId 資料行中的識別碼相同。 |
| InvocationId             | 發生此事件之調用的唯一數值識別碼。 |
| 名稱                     | 此事件所代表之活動或屬性的名稱。 |
| Time                     | 識別事件發生時間的時間戳記。 |
| 工具                     | 發生此事件時執行的工具。 此資料行的值是 CL 或 Link。 |
| 類型                     | 目前事件的型別。 這個值可以是活動或屬性。 |
| 值                    | 如果目前的事件是屬性，則此資料行包含其值。 當目前的事件是活動時，這個資料行就會保留空白。 |

### <a name="build-explorer-view-presets"></a>Build Explorer view 預設

| 預設名稱           | 慣用視圖模式 | 如何使用 |
|-----------------------|---------------------|------------|
| 活動統計資料   | 圖形/資料表       | 您可以使用此預設值來查看所有 Build Explorer 活動的匯總統計資料。 在 [資料表] 模式中，如果您的組建是由剖析、程式碼產生或連結器所主導，請一目了然。 每個活動的匯總持續時間會以遞減順序排序。 展開最上層節點以輕鬆找出哪些調用花費最多時間來進行這些最重要的活動。 您可以視需要調整 WPA 設定，以顯示平均或其他類型的匯總。 在 [圖形] 模式中，查看每個活動在您的組建期間何時處於作用中狀態。 |
| 調用           | 圖形               | 依開始時間排序的圖表視圖中的調用清單。 您可以使用它搭配 CPU (取樣) 視圖，以找出與低 CPU 使用率區域一致的調用。 偵測平行處理原則問題。 |
| 調用屬性 | 資料表               | 快速尋找有關特定編譯器或連結器調用的重要資訊。 判斷其版本、工作目錄或用來叫用它的完整命令列。 |
| 時間表             | 圖形               | 查看您的組建如何平行處理的橫條圖。 一眼就能識別平行處理的問題和瓶頸。 設定 WPA 以根據您的需求將不同意義指派給橫條。 選擇 [叫用描述] 作為 [最後群組] 資料行，以查看所有調用的色彩編碼橫條圖。 它可協助您快速找出花費在原因的時間。 然後，放大並選擇活動名稱做為最後分組的資料行，以查看最長的部分。 |

## <a name="files"></a>檔案儲存體

[檔案] 視圖可用來：

- 判斷最常包含的標頭，以及
- 協助您決定要在預先編譯的標頭中包含哪些內容 (PCH) 。

### <a name="files-view-data-columns"></a>檔案視圖資料行

| 資料行名稱              | 描述 |
|--------------------------|-------------|
| ActivityName             | 發出此檔案事件時進行中的活動。 目前，此值一律為 *剖析*。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 元件                | * |
| 計數                    | * |
| 深度                    | Include 樹狀結構中找到這個檔案的以零為起始的位置。 從 include 樹狀結構的根開始計算。 值為0時，通常會對應至 .c/.cpp 檔案。 |
| ExclusiveDuration        | * |
| IncludedBy               | 包含目前檔案之檔案的完整路徑。 |
| IncludedPath             | 目前檔案的完整路徑。 |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | 表示發出目前檔案事件之時間的時間戳記。 |
| 工具                     | * |

\* 此資料行的值與 [Build Explorer](#build-explorer-view-data-columns) 視圖中的值相同。

### <a name="files-view-presets"></a>檔案視圖預設

| 預設名稱 | 慣用視圖模式 | 如何使用 |
|-------------|---------------------|------------|
| 統計資料  | 資料表               | 查看清單中的遞減順序，以查看哪些檔案具有最高的匯總剖析時間。 您可以使用這項資訊來協助您重建標頭，或決定要包含在您的 PCH 中的內容。 |

## <a name="functions"></a>函式

函數視圖可用來識別具有過長程式碼產生時間的函式。

### <a name="functions-view-data-columns"></a>函數視圖資料行

| 資料行名稱              | 描述 |
|--------------------------|-------------|
| ActivityName             | 發出此函數事件時進行中的活動。 目前，此值一律為 *>nswag.codegeneration.csharp*。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 元件                | * |
| 計數                    | * |
| 持續時間                 | 此函式之程式碼產生活動的持續時間。 |
| FunctionName             | 要產生程式碼的函式名稱。 |
| InvocationId             | * |
| StartTime                | 表示發出目前的函式事件時的時間戳記。 |
| 工具                     | * |

\* 此資料行的值與 [Build Explorer](#build-explorer-view-data-columns) 視圖中的值相同。

### <a name="functions-view-presets"></a>函數視圖預設值

| 預設名稱 | 慣用視圖模式 | 如何使用 |
|-------------|---------------------|------------|
| 統計資料  | 資料表               | 查看以遞減順序排序的清單，查看哪些函式具有最高匯總的程式碼產生時間。 它們可能會提示您的程式碼 overuses 關鍵字的位置 **`__forceinline`** ，或某些函數可能太大。 |
| 時間表   | 圖形               | 查看此橫條圖，以瞭解花費最多時間產生的函式位置和持續時間。 查看它們是否與 Build Explorer 視圖中的瓶頸相符。 如果有的話，採取適當的動作來減少程式碼產生時間，並讓您的組建時間受益。 |

## <a name="see-also"></a>另請參閱

[開始使用 c + + Build Insights](../get-started-with-cpp-build-insights.md)\
[參考： vcperf 命令](vcperf-commands.md)\
[教學課程： Windows Performance Analyzer 基本概念](../tutorials/wpa-basics.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
