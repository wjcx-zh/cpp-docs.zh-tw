---
title: 逐步解說：建立影像處理網路
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 680037e0e14c3ebd9171cacf477520e025eecebe
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69512169"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>逐步解說：建立影像處理網路

本檔將示範如何建立可執行影像處理的非同步訊息區塊網路。

網路會根據其特性決定要在映射上執行的作業。 這個範例會使用*資料流程*模型，透過網路路由影像。 在資料流程模型中，程式的獨立元件會透過傳送訊息，彼此進行通訊。 當元件收到訊息時，它可以執行某個動作，然後將該動作的結果傳遞至另一個元件。 將此專案與*控制流程*模型進行比較，其中應用程式會使用控制結構（例如，條件陳述式、迴圈等等）來控制程式中的作業順序。

以資料流程為基礎的網路會建立工作的*管線*。 管線的每個階段都會同時執行整體工作的一部分。 以汽車製造的裝配線做比喻。 當每個車輛通過元件線時，一個站會組裝框架，另一個則會安裝引擎等等。 藉由讓多個車輛同時組合，[元件線] 可提供比一次組合一個完整車輛的輸送量更好。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列檔：

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：使用訊息區篩選](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

我們也建議您先瞭解 GDI + 的基本概念，再開始進行本逐步解說。

##  <a name="top"></a> 章節

本逐步解說包含下列各節：

- [定義影像處理功能](#functionality)

- [建立影像處理網路](#network)

- [完整範例](#complete)

##  <a name="functionality"></a>定義影像處理功能

本節顯示影像處理網路用來處理從磁片讀取之映射的支援功能。

下列`GetRGB`函式和`MakeColor`會分別將指定色彩的個別元件解壓縮和合併。

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

下列`ProcessImage`函式會呼叫指定的[std：： function](../../standard-library/function-class.md)物件，以轉換 gdi +[點陣圖](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)物件中每個圖元的色彩值。 函式會使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法，以平行方式處理點陣圖的每個資料列。 `ProcessImage`

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

下列函式、 `Grayscale` `Sepiatone`、、 `ColorMask`和`Darken`會呼叫`ProcessImage`函式，以轉換`Bitmap`物件中每個圖元的色彩值。 這些函式中的每一個都使用 lambda 運算式來定義一個圖元的色彩轉換。

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

下列`GetColorDominance`函式也會`ProcessImage`呼叫函數。 不過，此函式不會變更每個色彩的值，而是使用[concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md)物件來計算紅色、綠色或藍色色彩元件是否主導影像。

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

下列`GetEncoderClsid`函式會抓取編碼器之給定 MIME 類型的類別識別碼。 應用程式會使用此函式來抓取點陣圖的編碼器。

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[靠上](#top)]

##  <a name="network"></a>建立影像處理網路

本節說明如何建立異步訊息區塊的網路，以在指定目錄中的每個 JPEG （.jpg）影像上執行影像處理。 網路會執行下列影像處理作業：

1. 針對 Tom 所撰寫的任何影像，轉換為灰階。

1. 針對任何以紅色作為主要色彩的影像，移除綠色和藍色元件，然後將它變暗。

1. 若為任何其他影像，請套用棕色色調。

網路只會套用符合下列其中一個條件的第一個映射處理作業。 例如，如果影像是由 Tom 所撰寫，並以紅色作為其主要色彩，則影像只會轉換成灰階。

在網路執行每個影像處理作業之後，它會將映射以點陣圖（.bmp）檔案的形式儲存至磁片。

下列步驟示範如何建立可執行此影像處理網路的函式，並將該網路套用到指定目錄中的每個 JPEG 影像。

#### <a name="to-create-the-image-processing-network"></a>建立影像處理網路

1. 建立一個函式`ProcessImages`，此函式會採用磁片上的目錄名稱。

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. 在函式中， `countdown_event`建立變數。 `ProcessImages` 此逐步解說稍後會顯示類別。`countdown_event`

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. 建立[std：： map](../../standard-library/map-class.md)物件，使`Bitmap`物件與其原始檔案名稱產生關聯。

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. 新增下列程式碼，以定義影像處理網路的成員。

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. 新增下列程式碼以連接網路。

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. 新增下列程式碼，以傳送至網路的標頭，目錄中每個 JPEG 檔案的完整路徑。

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. `countdown_event`等候變數到達零。

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

下表描述網路的成員。

|成員|描述|
|------------|-----------------|
|`load_bitmap`|[Concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)物件，它會從`Bitmap`磁片載入物件，並將專案加入至`map`物件，以將影像與其原始檔案名稱產生關聯。|
|`loaded_bitmaps`|[Concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)物件，它會將載入的影像傳送至影像處理篩選。|
|`grayscale`|`transformer`物件，可將 tom 所撰寫的影像轉換成灰階。 它會使用影像的中繼資料來判斷其作者。|
|`colormask`|`transformer`物件，從具有紅色作為主要色彩的影像中移除綠色和藍色色彩元件。|
|`darken`|`transformer`物件，可將具有紅色的影像變暗為主要色彩。|
|`sepiatone`|`transformer`物件，其會對不是 Tom 所撰寫的影像套用棕色色調，而不是主要紅色。|
|`save_bitmap`|物件，將處理`image`的儲存至磁片做為點陣圖。 `transformer` `save_bitmap`抓取`map`物件的原始檔案名稱，並將其副檔名變更為 .bmp。|
|`delete_bitmap`|釋放映射記憶體的物件。`transformer`|
|`decrement`|作為網路中終端機節點的[concurrency：： call](../../parallel/concrt/reference/call-class.md)物件。 它會遞減`countdown_event`物件，以向主應用程式表示影像已處理過。|

訊息緩衝區很重要，因為`unbounded_buffer`做為物件，它會將`Bitmap`物件提供給多個接收者。 `loaded_bitmaps` 當目標區塊接受`Bitmap`物件時`unbounded_buffer` ，物件不會將該`Bitmap`物件提供給任何其他目標。 因此，將物件連結至`unbounded_buffer`物件的順序很重要。 、和訊息區塊都會使用篩選器，只接受特定`Bitmap`物件。 `sepiatone` `colormask` `grayscale` 訊息緩衝區是`loaded_bitmaps`訊息緩衝區的重要目標，因為它會接受其他消息`Bitmap`緩衝區拒絕的所有物件。 `decrement` 必須`unbounded_buffer`有物件，才能依序傳播訊息。 因此， `unbounded_buffer`物件會封鎖直到新的目標區塊連結到它，並在目前的目標區塊不接受該訊息時，接受該訊息。

如果您的應用程式要求多個訊息區塊處理訊息，而不只是一個會接受訊息的訊息區塊，您可以使用另一個訊息區塊類型，例如`overwrite_buffer`。 `overwrite_buffer`類別會一次保存一則訊息，但它會將該訊息傳播至它的每個目標。

下圖顯示影像處理網路：

![影像處理網路](../../parallel/concrt/media/concrt_imageproc.png "影像處理網路")

此`countdown_event`範例中的物件可讓影像處理網路在所有影像都已處理時，通知主要應用程式。 類別會使用[concurrency：： event](../../parallel/concrt/reference/event-class.md)物件，以在計數器值達到零時發出信號。 `countdown_event` 主要應用程式會在每次將檔案名傳送至網路時，遞增計數器。 網路的 [終端機] 節點會在每個影像處理之後，減少計數器。 在主應用程式流經指定的目錄之後，它會等候`countdown_event`物件指示其計數器已達到零。

下列範例顯示`countdown_event`類別:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[靠上](#top)]

##  <a name="complete"></a>完整範例

下列程式碼顯示完整範例。 函式會管理 gdi + 程式庫， `ProcessImages`並呼叫函數來處理`Sample Pictures`目錄中的 JPEG 檔案。 `wmain`

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

下圖顯示範例輸出。 每個來源影像高於其對應的已修改影像。

![範例輸出](../../parallel/concrt/media/concrt_imageout.png "範例輸出")

`Lighthouse`是由 Tom Alphin 所撰寫，因此會轉換成灰階。 `Chrysanthemum`、 `Desert`、 `Koala`和`Tulips`會以紅色作為主要色彩，因此會移除藍色和綠色色彩元件，且會變暗。 `Hydrangeas`、 `Jellyfish`和`Penguins`符合預設準則，因此為棕色 toned。

[[靠上](#top)]

### <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名`image-processing-network.cpp`為的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

**cl/DUNICODE/EHsc image-processing-network.cpp .cpp/link gdiplus.dll .lib**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
