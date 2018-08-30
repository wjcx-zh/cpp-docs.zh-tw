---
title: 逐步解說： 從使用者介面執行緒中移除工作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 663f8f3921788e64b26a57e95537ab44c757ea17
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211416"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>逐步解說：從使用者介面執行緒中移除工作
本文件將示範如何使用並行執行階段移動由使用者介面 (UI) 執行緒，在 Microsoft Foundation Classes (MFC) 應用程式中的背景工作執行緒所執行的工作。 這份文件也會示範如何改善耗時繪製作業的效能。  
  
 卸載的封鎖作業，從 UI 執行緒中移除工作，例如，繪圖，以背景工作執行緒可以改善您的應用程式的回應能力。 本逐步解說使用繪圖的常式，它會產生 Mandelbrot 碎形，來示範較長的封鎖作業。 產生 Mandelbrot 碎形的也是平行處理的良好候選項目，因為計算每個像素無關的所有其他計算。  
  
## <a name="prerequisites"></a>必要條件  
 在開始本逐步解說之前，請閱讀下列主題：  
  
-   [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
-   [平行演算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [PPL 中的取消](cancellation-in-the-ppl.md)  
  
 我們也建議您在開始本逐步解說之前，了解 MFC 應用程式開發和 GDI + 的基本概念。 如需有關 MFC 的詳細資訊，請參閱 < [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md)。 如需 GDI + 的詳細資訊，請參閱[GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798)。  
  
##  <a name="top"></a> 章節  
 本逐步解說包含下列各節：  
  
-   [建立 MFC 應用程式](#application)  
  
-   [實作 Mandelbrot 應用程式的序列版本](#serial)  
  
-   [從使用者介面執行緒中移除工作](#removing-work)  
  
-   [提高繪圖效能](#performance)  
  
-   [新增支援取消作業](#cancellation)  
  
##  <a name="application"></a> 建立 MFC 應用程式  
 本節說明如何建立基本的 MFC 應用程式。  
  
### <a name="to-create-a-visual-c-mfc-application"></a>建立 Visual c + + MFC 應用程式  
  
1.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  
  
2.  在**新的專案**對話方塊中，於**已安裝的範本**窗格中，選取**Visual c + +**，然後在**範本**窗格中，選取**MFC 應用程式**。 輸入專案名稱，例如`Mandelbrot`，然後按一下 **[確定]** 以顯示**MFC 應用程式精靈**。  
  
3.  在 **應用程式類型**窗格中，選取**單一文件**。 請確認**文件/檢視架構支援**核取方塊。  
  
4.  按一下 **完成**以建立專案，並關閉**MFC 應用程式精靈**。  
  
     請確認應用程式已成功建立，建置並執行它。 若要在建置應用程式時，**建置**功能表上，按一下**建置方案**。 如果應用程式建置成功，請按一下 執行應用程式**開始偵錯**上**偵錯**功能表。  
  
##  <a name="serial"></a> 實作 Mandelbrot 應用程式的序列版本  
 本節描述如何繪製 Mandelbrot 碎形。 此版本為 GDI + 繪製 Mandelbrot 碎形[點陣圖](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap)物件，並接著將該點陣圖的內容複製到用戶端視窗。  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>若要實作 Mandelbrot 應用程式的序列版本  
  
1.  在 stdafx.h 中新增下列`#include`指示詞：  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  在 ChildView.h 之後,`pragma`指示詞，定義`BitmapPtr`型別。 `BitmapPtr`型別可以讓指標`Bitmap`共用的多個元件的物件。 `Bitmap`任何元件不再參考它時，會刪除物件。  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  在 ChildView.h，加入下列程式碼`protected`一節`CChildView`類別：  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  在 ChildView.cpp，標記為註解或移除下列幾行。  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     在偵錯組建中，此步驟，防止應用程式使用`DEBUG_NEW`配置器，也就是使用 GDI + 不相容。  
  
5.  在 ChildView.cpp，加入`using`指示詞加入`Gdiplus`命名空間。  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  將下列程式碼新增至建構函式和解構函式的`CChildView`類別來初始化和關閉 GDI +。  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  實作 `CChildView::DrawMandelbrot` 方法。 這個方法會將 Mandelbrot 碎形繪製至指定`Bitmap`物件。  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  實作 `CChildView::OnPaint` 方法。 這個方法會呼叫`CChildView::DrawMandelbrot`，然後將複製的內容`Bitmap`物件轉換為視窗。  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. 請確認應用程式已成功更新建置並執行它。  
  
 下圖顯示 Mandelbrot 應用程式的結果。  
  
 ![Mandelbrot 應用程式](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 因為每個像素的計算相當耗費運算資源，UI 執行緒無法處理其他訊息，直到完成整體計算。 這可能會降低應用程式中的回應性。 不過，您可以藉由從 UI 執行緒中移除工作來減輕這個問題。  
  
 [[靠上](#top)]  
  
##  <a name="removing-work"></a> 從 UI 執行緒中移除工作  
 本節說明如何從 UI 執行緒 Mandelbrot 應用程式中移除繪圖的工作。 藉由將繪圖工作從 UI 執行緒移至背景工作執行緒，UI 執行緒可以處理訊息，因為背景工作執行緒在背景中產生的映像。  
  
 並行執行階段提供執行工作的三種方式：[工作群組](../../parallel/concrt/task-parallelism-concurrency-runtime.md)，[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)，並[輕量型工作](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 雖然您可以使用任何一種機制從 UI 執行緒中移除工作，此範例會使用[concurrency:: task_group](reference/task-group-class.md)物件，因為工作群組支援取消。 本逐步解說稍後會使用取消作業，以減少用戶端視窗調整大小時，會執行的工作數量，以及執行清除作業，當視窗被結束時。  
  
 此範例也會使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)物件，讓 UI 執行緒和背景工作執行緒來彼此通訊。 背景工作執行緒會產生映像後，它會傳送的指標`Bitmap`物件至`unbounded_buffer`物件，並繪製訊息至 UI 執行緒，然後發佈。 然後，在 UI 執行緒會接收來自`unbounded_buffer`物件`Bitmap`物件，並將它繪製至用戶端視窗。  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>從 UI 執行緒中移除繪圖的工作  
  
1.  在 stdafx.h 中新增下列`#include`指示詞：  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  在 ChildView.h，加入`task_group`並`unbounded_buffer`成員變數，以`protected`一節`CChildView`類別。 `task_group`物件會保存執行繪圖; 工作`unbounded_buffer`物件會保存已完成的 Mandelbrot 映像。  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  在 ChildView.cpp，加入`using`指示詞加入`concurrency`命名空間。  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  在 `CChildView::DrawMandelbrot`方法，在呼叫之後`Bitmap::UnlockBits`，呼叫[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式來傳遞`Bitmap`至 UI 執行緒的物件。 然後將 [小畫家] 訊息張貼至 UI 執行緒，並使工作區失效。  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  更新`CChildView::OnPaint`方法以接收更新`Bitmap`物件，並在用戶端視窗中繪製映像。  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     `CChildView::OnPaint`方法會建立工作，以產生 Mandelbrot 映像，如果不存在的訊息緩衝區中。 將不會包含訊息緩衝區`Bitmap`例如初始的 [小畫家] 訊息，而且當另一個視窗移動前用戶端視窗的物件。  
  
6.  請確認應用程式已成功更新建置並執行它。  
  
 UI 現在是回應速度更快的因為繪圖工作在背景中執行。  
  
 [[靠上](#top)]  
  
##  <a name="performance"></a> 提高繪圖效能  

 Mandelbrot 碎形的產生是平行處理的良好候選項目，因為計算每個像素無關的所有其他計算。 若要平行處理繪製程序，將轉換的外部`for`迴圈`CChildView::DrawMandelbrot`方法來呼叫[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法，如下所示。  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 計算每個點陣圖項目是獨立的因為您沒有同步處理存取點陣圖記憶體繪製作業。 這可讓效能隨著可用處理器數目增加而調整規模。  
  
 [[靠上](#top)]  
  
##  <a name="cancellation"></a> 新增支援取消作業  
 本章節描述如何處理視窗大小調整，以及如何終結視窗時，取消任何作用中繪製工作。  
  
 文件[PPL 中的取消](cancellation-in-the-ppl.md)說明取消在執行階段的運作方式。 取消是合作式;因此，它不會立即發生。 若要停止已取消的工作，執行階段會擲回執行階段期間的後續呼叫，從工作內部例外狀況。 上一節示範如何使用`parallel_for`演算法，以改善效能的繪製工作。 若要呼叫`parallel_for`可讓執行階段以停止工作，並因此可讓工作的取消作業。  
  
### <a name="cancelling-active-tasks"></a>正在取消作用中工作  
 Mandelbrot 應用程式會建立`Bitmap`物件的維度比對用戶端視窗的大小。 每次用戶端視窗調整大小時，應用程式會建立額外的背景工作，以產生新的視窗大小的影像。 應用程式不需要這些中繼映像;它需要的映像的最後一個視窗大小。 若要防止應用程式執行此額外工作，您可以取消任何作用中繪製工作中的訊息處理常式`WM_SIZE`和`WM_SIZING`訊息，然後重新排程繪製工作之後調整視窗大小。  
  
 若要重新調整視窗大小時，請取消作用中的繪製工作，應用程式會呼叫[concurrency::task_group::cancel](reference/task-group-class.md#cancel)方法中的處理常式`WM_SIZING`和`WM_SIZE`訊息。 處理常式`WM_SIZE`訊息也呼叫[2&gt;concurrency::task_group::wait&lt;2](reference/task-group-class.md#wait)方法，等待所有的作用中工作完成，然後重新排程繪製工作已更新的視窗大小。  
  
 用戶端視窗終結時，它會是很好的作法取消任何作用中繪製工作。 取消任何作用中的繪圖工作可確保背景工作執行緒執行不張貼訊息至 UI 執行緒之後用戶端視窗被結束後就行了。 應用程式會取消任何作用中繪圖工作的處理常式中`WM_DESTROY`訊息。  
  
### <a name="responding-to-cancellation"></a>回應取消作業  
 `CChildView::DrawMandelbrot`方法，用於執行繪製工作，必須回應取消。 執行階段使用例外狀況處理來取消工作，因為`CChildView::DrawMandelbrot`方法必須使用例外狀況安全機制來保證，所有資源都正確清除。 這個範例會使用*資源擷取即初始化*(RAII) 模式，可保證工作取消時，會解除鎖定點陣圖位元。  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Mandelbrot 應用程式中新增支援取消作業  
  
1.  在 ChildView.h，在`protected`一節`CChildView`類別中，新增宣告`OnSize`， `OnSizing`，和`OnDestroy`訊息對應函式。  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  在 ChildView.cpp，修改 將訊息對應到包含的處理常式`WM_SIZE`， `WM_SIZING`，和`WM_DESTROY`訊息。  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  實作 `CChildView::OnSizing` 方法。 這個方法會取消任何現有的繪製工作。  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  實作 `CChildView::OnSize` 方法。 這個方法會取消任何現有的繪製工作，並建立新的繪圖工作更新的用戶端視窗大小。  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  實作 `CChildView::OnDestroy` 方法。 這個方法會取消任何現有的繪製工作。  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  在 ChildView.cpp，定義`scope_guard`實作 RAII 模式的類別。  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  將下列程式碼加入`CChildView::DrawMandelbrot`方法之後呼叫`Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     此程式碼會藉由建立處理取消`scope_guard`物件。 當物件離開範圍時，它會解除鎖定點陣圖位元。  
  
8.  修改結尾`CChildView::DrawMandelbrot`方法來關閉`scope_guard`物件之後點陣圖位元會解除鎖定，但任何訊息傳送至 UI 執行緒之前。 這可確保之前解除鎖定點陣圖位元不會更新 UI 執行緒。  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. 請確認應用程式已成功更新建置並執行它。  
  
 當您調整視窗時，繪製工作是只能執行最後的視窗大小。 終結視窗時，也會取消所有作用中的繪製工作。  
  
 [[靠上](#top)]  
  
## <a name="see-also"></a>另請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [MFC 傳統型應用程式](../../mfc/mfc-desktop-applications.md)
