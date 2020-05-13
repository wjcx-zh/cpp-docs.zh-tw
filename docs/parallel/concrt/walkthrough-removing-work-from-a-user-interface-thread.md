---
title: 逐步解說：從使用者介面執行緒中移除工作
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377434"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>逐步解說：從使用者介面執行緒中移除工作

本文件展示如何使用併發運行時將 Microsoft 基礎類 (MFC) 應用程式中的使用者介面 (UI) 執行工作移動到輔助線程。 本文檔還演示如何提高冗長繪圖操作的性能。

通過將阻塞操作(例如繪圖)卸載到輔助線程,從UI線程中刪除工作可以提高應用程式的回應能力。 本演練使用生成曼德布羅特分形的繪圖例程來演示冗長的阻塞操作。 Mandelbrot 分形的生成也是並行化的良好候選項,因為每個像素的計算與所有其他計算無關。

## <a name="prerequisites"></a>Prerequisites

在開始本演練之前,請閱讀以下主題:

- [工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)

- [平行演算法](../../parallel/concrt/parallel-algorithms.md)

- [PPL 中的取消](cancellation-in-the-ppl.md)

我們還建議您在開始本演練之前瞭解 MFC 應用程式開發和 GDI+ 的基礎知識。 關於 MFC 的詳細資訊,請參閱[MFC 桌面應用程式](../../mfc/mfc-desktop-applications.md)。 有關 GDI+ 的詳細資訊,請參閱[GDI®](/windows/win32/gdiplus/-gdiplus-gdi-start)。

## <a name="sections"></a><a name="top"></a>部分

本逐步解說包含下列各節：

- [建立 MFC 應用程式](#application)

- [實現曼德布羅特應用程式的串列版本](#serial)

- [從使用者介面線程中移除工作](#removing-work)

- [提高繪圖效能](#performance)

- [新增取消支援](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>建立 MFC 應用程式

本節介紹如何創建基本的 MFC 應用程式。

### <a name="to-create-a-visual-c-mfc-application"></a>建立視覺化C++ MFC 應用程式

1. 使用**MFC 應用程式精靈**建立具有所有預設設定的 MFC 應用程式。 請參閱[演練:使用新的 MFC 外殼控件](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)瞭解如何打開 Visual Studio 版本的嚮導的說明。

1. 鍵入項目的名稱,例如,`Mandelbrot`然後按下 **「確定」** 以顯示**MFC 應用程式精靈**。

1. 在「**應用程式類型」** 窗格中,選擇 **「單一文檔**」 。 確保清除**文件/檢視體系結構支援**複選框。

1. 點選 **「完成」** 以建立項目並關閉**MFC 應用程式精靈**。

   通過生成並運行應用程式,驗證應用程式是否成功創建。 要生成應用程式,請在 **「生成」** 功能表上單擊 **「生成解決方案**」 。 如果應用程式生成成功,則通過按下 **「調試」** 功能表上的 **「開始調試**」來運行應用程式。

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>實現曼德布羅特應用程式的串列版本

本節介紹如何繪製曼德布羅特分形。 此版本將 Mandelbrot 分形繪製到 GDI+[位元圖](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)物件,然後將該位圖的內容複製到用戶端視窗。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>實現曼德布羅特應用程式的串列版本

1. 在*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中,添加以下`#include`指令:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. 在 ChildView.h`pragma`中 ,`BitmapPtr`在指令之後 ,定義類型。 類型`BitmapPtr`允許`Bitmap`指向 物件的指標由多個元件共用。 當`Bitmap`物件不再被任何元件引用時,將刪除該物件。

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. 在 ChildView.h 中,將`protected`以下代碼 加入`CChildView`為類別的部份:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. 在 ChildView.cpp 中,註釋掉或刪除以下行。

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   在除錯產生中,此步驟可防止應用程式使用分配器`DEBUG_NEW`,該分配器與 GDI+ 不相容。

1. 在 ChildView.cpp`using`中`Gdiplus`,向 命名空間添加一個指令。

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 將以下代碼添加到類的構造函數和析構函數中`CChildView`,以初始化和關閉 GDI+。

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. 實作 `CChildView::DrawMandelbrot` 方法。 此方法將曼德布羅特分形繪製到指定`Bitmap`物件。

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. 實作 `CChildView::OnPaint` 方法。 此方法調用`CChildView::DrawMandelbrot`物件的內容,然後`Bitmap`將 物件的內容複製到視窗。

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. 通過生成並運行應用程式,驗證應用程式是否已成功更新。

下圖顯示了曼德布羅特應用程序的結果。

![Mandelbrot 應用程式](../../parallel/concrt/media/mandelbrot.png "Mandelbrot 應用程式")

由於每個像素的計算在計算上成本高昂,因此在整體計算完成之前,UI 線程無法處理其他消息。 這可能會降低應用程式中的回應能力。 但是,您可以通過從 UI 線程中刪除工作來緩解此問題。

【[頂端](#top)

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>從 UI 執行緒中移除工作

本節演示如何從 Mandelbrot 應用程式中的 UI 線程中刪除繪圖工作。 通過將繪圖工作從 UI 線程移動到輔助線程,UI 線程可以在工作線程在後台生成圖像時處理消息。

並執行執行時提供三種執行工作的方法:[工作群組](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[非同步代理](../../parallel/concrt/asynchronous-agents.md)與[輕巧層工作](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 儘管可以使用這些機制中的任何一種從 UI 線程中刪除工作,此示例使用[併發::task_group](reference/task-group-class.md)物件,因為任務組支援取消。 本演練稍後將使用取消來減少調整用戶端視窗大小時執行的工作量,並在破壞視窗時執行清理。

此示例還使用[併發::unbounded_buffer](reference/unbounded-buffer-class.md)物件,以使 UI 線程和輔助線程能夠相互通信。 工作線程式產生映像後,它將指向`Bitmap`物件的指標發送到物件,`unbounded_buffer`然後將繪製消息發布到 UI 線程。 然後,UI 線程`unbounded_buffer``Bitmap`從物件接收物件並將其繪製到用戶端視窗。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>從 UI 執行緒中移除繪圖工作

1. 在*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中,添加以下`#include`指令:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. 在`task_group`ChildView.h`unbounded_buffer`中`protected``CChildView`,向 類的部分添加和成員變數。 物件`task_group`保存執行繪圖的任務;物件`unbounded_buffer`保存已完成的曼德布羅特圖像。

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. 在 ChildView.cpp`using`中`concurrency`,向 命名空間添加一個指令。

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. In `CChildView::DrawMandelbrot` the method, after `Bitmap::UnlockBits`the call to , call the [concurrency::send](reference/concurrency-namespace-functions.md#send) function to pass the `Bitmap` object to the UI thread. 然後向 UI 線程發布繪製消息,使工作區失效。

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. 更新`CChildView::OnPaint`方法以接收`Bitmap`更新 的物件,並將圖像繪製到用戶端視窗。

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   如果`CChildView::OnPaint`消息緩衝區中不存在一個圖像,該方法將創建一個任務來生成 Mandelbrot 映射。 在初始繪製消息以及另一`Bitmap`個視窗在用戶端視窗前面移動時,消息緩衝區將不包含物件。

1. 通過生成並運行應用程式,驗證應用程式是否已成功更新。

UI 現在回應更快,因為繪圖工作是在後台執行的。

【[頂端](#top)

## <a name="improving-drawing-performance"></a><a name="performance"></a>提高繪圖效能

Mandelbrot 分形的生成是並行化的良好候選項,因為每個像素的計算與所有其他計算無關。 要並行化繪圖過程,請將方法中的`for``CChildView::DrawMandelbrot`外部迴圈轉換為對[併發::p阿拉雷爾演演演算法的](reference/concurrency-namespace-functions.md#parallel_for)調用,如下所示。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

由於每個點陣圖元素的計算都是獨立的,因此不必同步訪問位圖記憶體的繪圖操作。 這使得性能能夠隨著可用處理器數量的增加而擴展。

【[頂端](#top)

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>新增取消支援

本節介紹如何處理窗口調整大小,以及如何在視窗被銷毀時取消任何活動繪圖任務。

[PPL 中的"取消"](cancellation-in-the-ppl.md)文檔說明瞭取消在運行時的工作原理。 取消是合作的;因此,它不會立即發生。 要停止已取消的任務,運行時在後續調用從任務到運行時時引發內部異常。 上一節演示如何使用`parallel_for`該演演演算法來提高繪圖任務的性能。 調用`parallel_for`使 運行時停止任務,從而使取消工作。

### <a name="cancelling-active-tasks"></a>取消活動工作

Mandelbrot 應用程式`Bitmap`創建 其維度與用戶端視窗大小匹配的物件。 每次調整用戶端視窗的大小時,應用程式都會創建一個額外的後台任務,以生成新視窗大小的映射。 應用程式不需要這些中間圖像;因此,應用程式不需要這些中間圖像。它只需要最終視窗大小的圖像。 為了防止應用程式執行此附加工作,可以取消`WM_SIZE`和`WM_SIZING`消息的消息處理程式中的任何活動繪圖任務,然後在調整視窗大小后重新安排繪圖工作。

要在調整視窗大小時取消活動繪圖任務,應用程式將`WM_SIZING``WM_SIZE`調用 和幣處理程式中的[併發::task_group::取消](reference/task-group-class.md#cancel)方法。 消息的`WM_SIZE`處理程式還調用[併發:::task_group::等待](reference/task-group-class.md#wait)方法等待所有活動任務完成,然後為更新的視窗大小重新安排繪圖任務。

銷毀客戶端視窗時,最好取消任何活動繪圖任務。 取消任何活動繪圖任務可確保工作線程不會在用戶端窗口銷毀後向 UI 線程發送消息。 應用程式取消`WM_DESTROY`消息處理程式中的任何活動繪圖任務。

### <a name="responding-to-cancellation"></a>回應取消

執行`CChildView::DrawMandelbrot`繪圖任務的方法必須回應取消。 由於執行時使用異常處理來取消任務,`CChildView::DrawMandelbrot`因此該方法必須使用異常安全機制來保證正確清理所有資源。 本示例使用*資源獲取初始化*(RAII) 模式來保證在取消任務時未鎖定位圖位。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>在曼德布羅特應用程式中添加對取消的支援

1. 在 ChildView.h`protected`中`CChildView`,在類部分`OnSize`中`OnSizing`,`OnDestroy`為、 消息映射函數添加聲明。

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. 在 ChildView.cpp 中,修改消息映射`WM_SIZE`以`WM_SIZING`包含的處理`WM_DESTROY`程式。

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. 實作 `CChildView::OnSizing` 方法。 此方法取消任何現有的繪圖任務。

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. 實作 `CChildView::OnSize` 方法。 此方法取消任何現有繪圖任務,並為更新的用戶端視窗大小創建新的繪圖任務。

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. 實作 `CChildView::OnDestroy` 方法。 此方法取消任何現有的繪圖任務。

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. 在 ChildView.cpp`scope_guard`中 ,定義實現 RAII 模式的類。

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. 呼叫 後,將`CChildView::DrawMandelbrot`以下 代碼加入`Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   此代碼通過創建`scope_guard`對象來處理取消。 當物件離開範圍時,它將解鎖位圖位。

1. 修改方法的`CChildView::DrawMandelbrot`末尾以在位圖`scope_guard`位 解鎖后(但在將任何消息發送到 UI 線程之前)關閉物件。 這可確保在未鎖定位圖位之前不更新 UI 線程。

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. 通過生成並運行應用程式,驗證應用程式是否已成功更新。

調整視窗大小時,僅針對最終視窗大小執行繪圖工作。 銷毀視窗時,任何活動繪圖任務也會被取消。

【[頂端](#top)

## <a name="see-also"></a>另請參閱

[併發運行時演練](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[MFC 傳統型應用程式](../../mfc/mfc-desktop-applications.md)
