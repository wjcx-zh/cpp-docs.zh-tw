---
title: 參考： Windows Performance Analyzer views
description: Windows Performance C++ Analyzer 中提供之 Build Insights views 的參考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eb3e20ed3ca4231b10efaf36310f6fbc0f5980bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332233"
---
# <a name="reference-windows-performance-analyzer-views"></a>參考： Windows Performance Analyzer views

::: moniker range="<=vs-2017"

Visual Studio C++ 2019 中提供 Build Insights 工具。 若要查看該版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

本文提供 Windows Performance Analyzer （WPA） C++中所提供的每個組建深入解析視圖的詳細資料。 使用此頁面來尋找：

- 資料行描述;和
- 每個視圖的可用預設值，包括其預定用途和慣用的瀏覽模式。

如果您不熟悉 WPA，建議您先熟悉[適用于C++ BUILD Insights 的 wpa 基本概念](/cpp/build-insights/tutorials/wpa-basics)。

## <a name="build-explorer"></a>Build 總管

組建瀏覽器視圖用來：

- 診斷平行處理原則問題，
- 判斷您的組建時間是否藉由剖析、程式碼產生或連結，以及
- 找出瓶頸和異常長的組建活動。

### <a name="build-explorer-view-data-columns"></a>組建瀏覽器視圖資料行

| 資料行名稱 | 描述 |
|-|-|
| BuildTimelineDescription | 文字描述發生目前活動或屬性的時間軸。 |
| BuildTimelineId          | 目前活動或屬性發生所在時間軸的以零為基底的識別碼。 |
| 元件                | 發出目前事件時所編譯或連結的元件。 當沒有任何元件與此事件關聯時，這個資料行的值就是 *\<調用 X 資訊\>* 。 X 是在發出事件時所執行之調用的唯一數值識別碼。 此識別碼與此事件的 InvocationId 資料行中的識別碼相同。 |
| Count                    | 此資料列所表示的活動或屬性數目。 這個值一律是1，只有在群組多個資料列時，才適用于匯總案例。 |
| ExclusiveCPUTime         | 此活動所使用的 CPU 時間量（以毫秒為單位）。 在子活動中所花費的時間不會包含在此數量內。 |
| ExclusiveDuration        | 活動的毫秒持續時間。 子活動的持續時間不會包含在此數量內。 |
| InclusiveCPUTime         | 這個活動和所有子活動所使用的 CPU 時間量（以毫秒為單位）。 |
| InclusiveDuration        | 此活動的毫秒持續時間，包括所有子活動。 |
| InvocationDescription    | 發生此事件之調用的文字描述。 此描述包括*cl .exe*或*link*.exe，以及唯一的數值調用識別碼。 如果適用的話，它會包含在叫用期間編譯或連結之元件的完整路徑。 對於不會建立任何元件或建立多個元件的調用，此路徑是空白的。 調用識別碼與 InvocationId 資料行中的相同。 |
| InvocationId             | 發生此事件之調用的唯一數值識別碼。 |
| 名稱                     | 這個事件所表示之活動或屬性的名稱。 |
| Time                     | 識別事件發生時機的時間戳記。 |
| 工具                     | 此事件發生時執行的工具。 此資料行的值可以是 CL 或 Link。 |
| 類型                     | 目前事件的類型。 這個值可以是 [活動] 或 [屬性]。 |
| 值                    | 如果目前事件是屬性，則此資料行包含其值。 當目前的事件為活動時，這個資料行會保留空白。 |

### <a name="build-explorer-view-presets"></a>組建瀏覽器視圖預設值

| 預設名稱           | 慣用的視圖模式 | 使用方式 |
|-----------------------|---------------------|------------|
| 活動統計資料   | 圖表/資料表       | 使用此預設值來查看所有組建瀏覽器活動的匯總統計資料。 在 [資料表模式] 中，如果您的組建是藉由剖析、程式碼產生或連結器來進行，請一目了然。 每個活動的匯總持續時間會以遞減順序排序。 藉由展開最上層節點來切入，輕鬆地找出這些最重要活動最耗費時間的調用。 如有需要，您可以調整 WPA 設定，以顯示平均值或其他類型的匯總。 在 [圖形模式] 中，查看組建期間每個活動何時作用中。 |
| 機器           | 圖形               | 在圖表視圖中，按 [開始時間] 排序的調用清單。 您可以將它與 [CPU （取樣）] 視圖一起使用，以尋找與低 CPU 使用率區域相符的調用。 偵測平行處理原則的問題。 |
| 調用屬性 | Table               | 快速找出有關特定編譯器或連結器調用的重要資訊。 判斷其版本、工作目錄，或用來叫用它的完整命令列。 |
| 時間表             | 圖形               | 查看如何平行處理組建的橫條圖。 一眼就能找出平行處理的問題和瓶頸。 設定 WPA 根據您的需求，將不同的意義指派給橫條。 選擇 [叫用描述] 做為最後一個分組的資料行，以查看所有調用的色彩編碼橫條圖。 它可協助您快速識別耗時的原因。 然後，放大並選擇 [活動名稱] 做為最後一個分組的資料行，以查看最長的部分。 |

## <a name="files"></a>檔案

檔案視圖用來：

- 判斷最常包含的標頭，以及
- 協助您決定要包含在預先編譯的標頭（PCH）中的內容。

### <a name="files-view-data-columns"></a>檔案視圖資料行

| 資料行名稱              | 描述 |
|--------------------------|-------------|
| ActivityName             | 發出此檔案事件時，正在進行中的活動。 目前，此值一律會進行*剖析*。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 元件                | * |
| Count                    | * |
| 深度                    | 在其中找到此檔案之 include 樹狀結構中以零為起始的位置。 計算會從包含樹狀結構的根目錄開始。 值為0通常會對應至 .c/.cpp 檔案。 |
| ExclusiveDuration        | * |
| IncludedBy               | 包含目前檔案之檔案的完整路徑。 |
| IncludedPath             | 目前檔案的完整路徑。 |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | 時間戳記，表示發出目前檔案事件的時間。 |
| 工具                     | * |

\* 這個資料行的值與 [[組建瀏覽器](#build-explorer-view-data-columns)] 視圖中的相同。

### <a name="files-view-presets"></a>檔案視圖預設值

| 預設名稱 | 慣用的視圖模式 | 使用方式 |
|-------------|---------------------|------------|
| 統計資料  | Table               | 查看清單的遞減順序，以瞭解哪些檔案具有最高的匯總剖析時間。 使用這項資訊可協助您重建標頭，或決定要包含在 PCH 中的內容。 |

## <a name="functions"></a>Functions

函式 view 是用來識別程式碼產生時間過長的函數。

### <a name="functions-view-data-columns"></a>函數視圖資料行

| 資料行名稱              | 描述 |
|--------------------------|-------------|
| ActivityName             | 發出此函式事件時進行中的活動。 目前，此值一律為*nswag.codegeneration.csharp*。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 元件                | * |
| Count                    | * |
| Duration                 | 此函式之程式碼產生活動的持續時間。 |
| FunctionName             | 要產生程式碼的函式名稱。 |
| InvocationId             | * |
| StartTime                | 表示目前函式事件發出時的時間戳記。 |
| 工具                     | * |

\* 這個資料行的值與 [[組建瀏覽器](#build-explorer-view-data-columns)] 視圖中的相同。

### <a name="functions-view-presets"></a>函數視圖預設值

| 預設名稱 | 慣用的視圖模式 | 使用方式 |
|-------------|---------------------|------------|
| 統計資料  | Table               | 藉由以遞減順序查看清單，查看哪些函式具有最高的匯總程式碼產生時間。 他們可能會提示您的程式碼 overuses **__forceinline**關鍵字，或某些函數可能太大。 |
| 時間表   | 圖形               | 查看此橫條圖，以瞭解花費最多時間產生之函式的位置和持續時間。 查看它們是否符合組建瀏覽器視圖中的瓶頸。 如果有，請採取適當的行動來減少其程式碼產生時間，並讓您的組建時間受益。 |

## <a name="see-also"></a>另請參閱

[開始使用C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[參考： vcperf 命令](vcperf-commands.md)\
[教學課程： Windows Performance Analyzer 基本概念](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
