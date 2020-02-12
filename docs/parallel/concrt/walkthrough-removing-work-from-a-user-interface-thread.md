---
title: 逐步解說：從使用者介面執行緒中移除工作
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 518044d4e3adea44c3776793c8277939076066d6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140702"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>逐步解說：從使用者介面執行緒中移除工作

本檔示範如何使用並行執行階段，將 Microsoft Foundation class （MFC）應用程式中的使用者介面（UI）執行緒所執行的工作移至背景工作執行緒。 本檔也會示範如何改善冗長繪圖作業的效能。

藉由卸載封鎖作業（例如，繪製）至背景工作執行緒，從 UI 執行緒中移除工作，可以改善應用程式的回應能力。 本逐步解說會使用繪製常式來產生 Mandelbrot 碎形，以示範冗長的封鎖作業。 產生 Mandelbrot 碎形也是平行處理的理想候選，因為每個圖元的計算都與其他所有計算無關。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列主題：

- [工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

- [平行演算法](../../parallel/concrt/parallel-algorithms.md)

- [PPL 中的取消](cancellation-in-the-ppl.md)

我們也建議您先瞭解 MFC 應用程式開發和 GDI + 的基本概念，再開始進行本逐步解說。 如需 MFC 的詳細資訊，請參閱[Mfc 桌面應用程式](../../mfc/mfc-desktop-applications.md)。 如需 GDI + 的詳細資訊，請參閱[Gdi +](/windows/win32/gdiplus/-gdiplus-gdi-start)。

## <a name="top"></a> 章節

本逐步解說包含下列各節：

- [建立 MFC 應用程式](#application)

- [執行 Mandelbrot 應用程式的序列版本](#serial)

- [從使用者介面執行緒中移除工作](#removing-work)

- [改善繪圖效能](#performance)

- [新增取消的支援](#cancellation)

## <a name="application"></a>建立 MFC 應用程式

本節說明如何建立基本 MFC 應用程式。

### <a name="to-create-a-visual-c-mfc-application"></a>建立 Visual C++ MFC 應用程式

1. 使用**Mfc 應用程式精靈**來建立具有所有預設設定的 mfc 應用程式。 如需如何為您的 Visual Studio 版本開啟嚮導的指示，請參閱[逐步解說：使用新的 MFC Shell 控制項](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)。

1. 輸入專案的名稱，例如 `Mandelbrot`，然後按一下 **[確定]** 以顯示 [ **MFC 應用程式精靈]** 。

1. 在 [**應用程式類型**] 窗格中，選取 [**單一檔**]。 確定已清除 [**檔/視圖架構支援**] 核取方塊。

1. 按一下 **[完成]** 以建立專案，然後關閉 [ **MFC 應用程式精靈]** 。

   藉由建立並執行應用程式，確認已成功建立。 若要建立應用程式，請在 [**建立**] 功能表上，按一下 [**建立方案**]。 如果成功建立應用程式，請按一下 [**調試**程式] 功能表上的 [**啟動調試**程式] 來執行應用程式。

## <a name="serial"></a>執行 Mandelbrot 應用程式的序列版本

本節說明如何繪製 Mandelbrot 碎形。 此版本會將 Mandelbrot 碎形繪製至 GDI +[點陣圖](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)物件，然後將該點陣圖的內容複寫到用戶端視窗。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>若要執行 Mandelbrot 應用程式的序列版本

1. 在*pch* （Visual Studio 2017 和更早版本的*stdafx.h* ）中，新增下列 `#include` 指示詞：

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. 在 ChildView 中，于 `pragma` 指示詞之後定義 `BitmapPtr` 類型。 `BitmapPtr` 類型可讓多個元件共用 `Bitmap` 物件的指標。 當任何元件不再參考 `Bitmap` 物件時，就會將其刪除。

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. 在 ChildView 中，將下列程式碼新增至 `CChildView` 類別的 `protected` 區段中：

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. 在 ChildView 中，將下列幾行標記為批註或移除。

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   在 Debug 組建中，此步驟可防止應用程式使用 `DEBUG_NEW` 配置器，這與 GDI + 不相容。

1. 在 ChildView 中，將 `using` 指示詞新增至 `Gdiplus` 命名空間。

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 將下列程式碼加入至 `CChildView` 類別的函數和析構函式，以初始化和關閉 GDI +。

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. 實作 `CChildView::DrawMandelbrot` 方法。 這個方法會將 Mandelbrot 碎形繪製到指定的 `Bitmap` 物件。

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. 實作 `CChildView::OnPaint` 方法。 這個方法會呼叫 `CChildView::DrawMandelbrot`，然後將 `Bitmap` 物件的內容複寫到視窗。

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. 藉由建立並執行應用程式，確認已成功更新應用程式。

下圖顯示 Mandelbrot 應用程式的結果。

![Mandelbrot 應用程式](../../parallel/concrt/media/mandelbrot.png "Mandelbrot 應用程式")

由於每個圖元的計算成本很高，因此 UI 執行緒無法處理額外的訊息，直到整體計算完成為止。 這可能會降低應用程式的回應能力。 不過，您可以從 UI 執行緒中移除工作，以減輕這個問題。

[[靠上](#top)]

## <a name="removing-work"></a>從 UI 執行緒中移除工作

本節說明如何從 Mandelbrot 應用程式中的 UI 執行緒移除繪製工作。 藉由將繪圖工作從 UI 執行緒移至背景工作執行緒，UI 執行緒可以處理訊息，因為工作者執行緒會在背景中產生影像。

並行執行階段提供三種執行工作的方式：[工作組](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[非同步代理](../../parallel/concrt/asynchronous-agents.md)程式和[輕量](../../parallel/concrt/task-scheduler-concurrency-runtime.md)工作。 雖然您可以使用上述任何一種機制從 UI 執行緒中移除工作，但此範例會使用[concurrency：： task_group](reference/task-group-class.md)物件，因為工作組支援取消。 此逐步解說稍後會使用取消來減少調整用戶端視窗大小時所執行的工作量，並在終結視窗時執行清除。

這個範例也會使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)物件，讓 UI 執行緒和背景工作執行緒彼此進行通訊。 在背景工作執行緒產生影像之後，它會將 `Bitmap` 物件的指標傳送至 `unbounded_buffer` 物件，然後將繪製訊息張貼至 UI 執行緒。 然後，UI 執行緒會從 `unbounded_buffer` 物件接收 `Bitmap` 物件，並將它繪製至用戶端視窗。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>從 UI 執行緒中移除繪製工作

1. 在*pch* （Visual Studio 2017 和更早版本的*stdafx.h* ）中，新增下列 `#include` 指示詞：

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. 在 ChildView 中，將 `task_group` 和 `unbounded_buffer` 成員變數新增至 `CChildView` 類別的 `protected` 區段。 `task_group` 物件會保存執行繪製的工作;`unbounded_buffer` 物件會保存已完成的 Mandelbrot 映射。

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. 在 ChildView 中，將 `using` 指示詞新增至 `concurrency` 命名空間。

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. 在 `CChildView::DrawMandelbrot` 方法中，呼叫 `Bitmap::UnlockBits`之後，請呼叫[concurrency：： send](reference/concurrency-namespace-functions.md#send)函式，將 `Bitmap` 物件傳遞至 UI 執行緒。 然後將繪製訊息張貼至 UI 執行緒，並使工作區失效。

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 更新 `CChildView::OnPaint` 方法，以接收已更新的 `Bitmap` 物件，並在用戶端視窗中繪製影像。

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` 方法會建立一個工作，以產生 Mandelbrot 的映射（如果訊息緩衝區中不存在）。 訊息緩衝區不會包含初始繪製訊息時的 `Bitmap` 物件，以及在用戶端視窗前方移動另一個視窗時的情況。

1. 藉由建立並執行應用程式，確認已成功更新應用程式。

UI 現在更具回應性，因為繪圖工作是在背景中執行。

[[靠上](#top)]

## <a name="performance"></a>改善繪圖效能

產生 Mandelbrot 碎形是平行處理的理想候選，因為每個圖元的計算都與其他所有計算無關。 若要平行處理繪圖程式，請將 `CChildView::DrawMandelbrot` 方法中的外部 `for` 迴圈轉換成[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法的呼叫，如下所示。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

因為每個點陣圖元素的計算都是獨立的，所以您不需要同步處理存取點陣圖記憶體的繪圖作業。 這可讓您在可用的處理器數目增加時調整效能。

[[靠上](#top)]

## <a name="cancellation"></a>新增取消的支援

本節說明如何處理視窗的調整大小，以及如何在視窗終結時取消任何使用中的繪製工作。

[PPL 中](cancellation-in-the-ppl.md)的檔取消說明取消作業在執行時間中的運作方式。 取消是合作的;因此，它不會立即發生。 若要停止已取消的工作，執行時間會在後續從工作到執行時間的呼叫期間擲回內部例外狀況。 上一節說明如何使用 `parallel_for` 演算法來改善繪製工作的效能。 `parallel_for` 的呼叫可讓執行時間停止工作，因此可讓取消作業正常執行。

### <a name="cancelling-active-tasks"></a>取消作用中的工作

Mandelbrot 應用程式會建立 `Bitmap` 物件，其維度符合用戶端視窗的大小。 每次調整用戶端視窗大小時，應用程式會建立一個額外的背景工作，以產生新視窗大小的影像。 應用程式不需要這些中繼映射;它只需要最終視窗大小的影像。 若要防止應用程式執行這個額外的工作，您可以取消 `WM_SIZE` 和 `WM_SIZING` 訊息的訊息處理常式中的任何使用中繪製工作，然後在調整視窗大小後重新排定繪製工作。

若要在調整大小視窗時取消使用中的繪製工作，應用程式會在 `WM_SIZING` 和 `WM_SIZE` 訊息的處理常式中，呼叫[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)方法。 `WM_SIZE` 訊息的處理常式也會呼叫[concurrency：： task_group：： wait](reference/task-group-class.md#wait)方法，等待所有作用中的工作完成，然後重新排程已更新視窗大小的繪製工作。

當用戶端視窗終結時，最好是取消任何使用中的繪製工作。 取消任何使用中的繪圖工作，可確保工作者執行緒不會在用戶端視窗終結之後，將訊息張貼至 UI 執行緒。 應用程式會取消 `WM_DESTROY` 訊息之處理常式中的任何使用中繪製工作。

### <a name="responding-to-cancellation"></a>回應取消

執行繪製工作的 `CChildView::DrawMandelbrot` 方法必須回應取消。 由於執行時間會使用例外狀況處理來取消工作，因此 `CChildView::DrawMandelbrot` 的方法必須使用例外狀況安全的機制，以確保所有資源都已正確清除。 這個範例會使用*資源*取得的初始化（RAII）模式，以確保在取消工作時，會解除鎖定點陣圖位。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>在 Mandelbrot 應用程式中新增取消支援

1. 在 ChildView 中，于 `CChildView` 類別的 `protected` 區段中，加入 `OnSize`、`OnSizing`和 `OnDestroy` 訊息對應函數的宣告。

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. 在 ChildView 中，修改訊息對應以包含 `WM_SIZE`、`WM_SIZING`和 `WM_DESTROY` 訊息的處理常式。

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. 實作 `CChildView::OnSizing` 方法。 這個方法會取消任何現有的繪圖工作。

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. 實作 `CChildView::OnSize` 方法。 這個方法會取消任何現有的繪圖工作，並為更新的用戶端視窗大小建立新的繪製工作。

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. 實作 `CChildView::OnDestroy` 方法。 這個方法會取消任何現有的繪圖工作。

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. 在 ChildView 中，定義可執行 RAII 模式的 `scope_guard` 類別。

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 在呼叫 `Bitmap::LockBits`之後，將下列程式碼新增至 `CChildView::DrawMandelbrot` 方法：

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   這個程式碼會藉由建立 `scope_guard` 物件來處理取消作業。 當物件離開範圍時，它會解除鎖定點陣圖位。

1. 修改 `CChildView::DrawMandelbrot` 方法的結尾，以在點陣圖位解除鎖定後，但在任何訊息傳送至 UI 執行緒之前，關閉 `scope_guard` 物件。 這可確保在取消鎖定點陣圖位之前，不會更新 UI 執行緒。

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. 藉由建立並執行應用程式，確認已成功更新應用程式。

當您調整視窗大小時，只會針對最終視窗大小執行繪製工作。 當視窗損毀時，也會取消任何作用中的繪圖工作。

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[MFC 傳統型應用程式](../../mfc/mfc-desktop-applications.md)
