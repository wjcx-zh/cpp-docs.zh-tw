---
title: "逐步解說：從使用者介面執行緒中移除工作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "從使用者介面執行緒中移除工作 [並行執行階段]"
  - "使用者介面執行緒, 從中移除工作 [並行執行階段]"
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
caps.latest.revision: 14
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：從使用者介面執行緒中移除工作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件示範如何使用並行執行階段將使用者介面 \(UI\) 執行緒在 Microsoft Foundation Classes \(MFC\) 應用程式中執行的工作移動到背景工作執行緒。  本文件同時示範如何改善冗長繪製作業的效能。  
  
 透過卸載封鎖作業 \(例如，繪製\) 從 UI 執行緒中移除工作並移到背景工作執行緒，可以改善應用程式的回應能力。  本逐步解說使用可產生 Mandelbrot 碎形的繪製常式來示範冗長的封鎖作業。  產生 Mandelbrot 碎形也是很不錯的候選平行化作業，因為每一個像素的計算作業與其他所有計算作業都無關。  
  
## 必要條件  
 在您開始閱讀此逐步解說前，請先參閱下列主題：  
  
-   [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
-   [平行演算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [取消](../../parallel/concrt/cancellation-in-the-ppl.md)  
  
 我們也建議您在開始這個逐步解說之前，先了解 MFC 應用程式開發與 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的基本概念。  如需 MFC 的詳細資訊，請參閱 [MFC 桌面應用程式](../../mfc/mfc-desktop-applications.md)。  如需 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 的詳細資訊，請參閱 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
##  <a name="top"></a> 章節  
 此逐步解說包含下列章節：  
  
-   [建立 MFC 應用程式](#application)  
  
-   [實作 Mandelbrot 應用程式的系列版本](#serial)  
  
-   [從使用者介面執行緒中移除工作](#removing-work)  
  
-   [提升繪製效能](#performance)  
  
-   [加入取消的支援](#cancellation)  
  
##  <a name="application"></a> 建立 MFC 應用程式  
 本節說明如何建立基本的 MFC 應用程式。  
  
### 若要建立 Visual C\+\+ MFC 應用程式  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[**已安裝的範本**\] 窗格中的 \[**Visual C\+\+**\]，然後選取 \[**範本**\] 窗格中的 \[**MFC 應用程式**\]。  輸入專案的名稱 \(例如 `Mandelbrot`\)，然後按一下 \[**確定**\] 以顯示 \[**MFC 應用程式精靈**\]。  
  
3.  選取 \[**應用程式類型**\] 窗格中的 \[**單一文件**\]。  確定已清除 \[**文件\/檢視架構支援**\] 核取方塊。  
  
4.  按一下 \[**完成**\] 以建立專案並關閉 \[**MFC 應用程式精靈**\]。  
  
     建置並執行應用程式，以確認應用程式建立成功。  若要建置應用程式，請按一下 \[**建置**\] 功能表上的 \[**建置方案**\]。  如果應用程式建置成功，請按一下 \[**偵錯**\] 功能表上的 \[**開始偵錯**\] 以執行應用程式。  
  
##  <a name="serial"></a> 實作 Mandelbrot 應用程式的系列版本  
 本節說明如何繪製 Mandelbrot 碎形。  這個版本會將 Mandelbrot 碎形繪製到 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [Bitmap](https://msdn.microsoft.com/en-us/library/ms534420.aspx) 物件，然後將該點陣圖的內容複製到用戶端視窗。  
  
#### 若要實作 Mandelbrot 應用程式的系列版本  
  
1.  在 stdafx.h 中，加入下列 `#include` 指示詞：  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  在 ChildView.h 中，與 `pragma` 指示詞後面，定義 `BitmapPtr` 型別。  `BitmapPtr` 型別可以讓多個元件共用 `Bitmap` 物件的指標。  當任何元件都不再參考 `Bitmap` 物件時，該物件就會被刪除。  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  在 ChildView.h 中，將下列程式碼加入至 `CChildView` 類別的 `protected` 區段：  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  在 ChildView.cpp 中，將下列程式行標記為註解或予以移除。  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     在偵錯版中，這個步驟可防止應用程式使用與 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] 不相容的 `DEBUG_NEW` 配置器。  
  
5.  在 ChildView.cpp 中，藉 `using` 指示詞將 `Gdiplus` 命名空間加入。  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  將下列程式碼加入至 `CChildView` 類別的建構函式和解構函式，以初始化和關閉 [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)]。  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  實作 `CChildView::DrawMandelbrot` 方法。  這個方法會將 Mandelbrot 碎形繪製到指定的 `Bitmap` 物件。  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  實作 `CChildView::OnPaint` 方法。  這個方法會呼叫 `CChildView::DrawMandelbrot`，然後將 `Bitmap` 物件的內容複製到視窗。  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. 建置並執行應用程式，藉以確認應用程式更新成功。  
  
 下圖顯示 Mandelbrot 應用程式的結果。  
  
 ![Mandelbrot 應用程式](../../parallel/concrt/media/mandelbrot.png "Mandelbrot")  
  
 因為計算每一個像素需耗費大量計算資源，所以 UI 執行緒要等到整體計算完成時，才能處理其他訊息。  這會使應用程式的回應能力降低。  不過，您可以從 UI 執行緒中移除工作，以減輕這個問題。  
  
 \[[上方](#top)\]  
  
##  <a name="removing-work"></a> 從 UI 執行緒中移除工作  
 本節顯示如何在 Mandelbrot 應用程式中從 UI 執行緒移除繪製工作。  將繪製工作從 UI 執行緒移到背景工作執行緒，UI 執行緒便可在背景工作執行緒於背景產生影像時處理訊息。  
  
 並行執行階段提供三種可供執行工作的方式：[工作群組](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)和[輕量型工作](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  雖然您可以使用上述任何一種機制從 UI 執行緒中移除工作，但是這個範例將使用 [concurrency::task\_group](../Topic/task_group%20Class.md) 物件，因為工作群組可支援取消作業。  本逐步解說稍後會利用取消作業來減少調整用戶端視窗大小時所執行的工作量，並且在視窗終結時執行清除。  
  
 此外，本範例也使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 物件，讓 UI 執行緒和背景工作執行緒能夠互相通訊。  在背景工作執行緒產生影像之後，便會將 `Bitmap` 物件的指標傳送到 `unbounded_buffer` 物件，然後張貼一則繪製訊息至 UI 執行緒。  UI 執行緒會從 `unbounded_buffer` 物件收到 `Bitmap` 物件，並將它繪製到用戶端視窗。  
  
#### 若要從 UI 執行緒中移除繪製工作  
  
1.  在 stdafx.h 中，加入下列 `#include` 指示詞：  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  在 ChildView.h 中，將下列 `task_group` 和 `unbounded_buffer` 成員變數加入至 `CChildView` 類別的 `protected` 區段：  `task_group` 物件會包含執行繪製的工作；`unbounded_buffer` 物件則包含已完成的 Mandelbrot 影像。  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  在 ChildView.cpp 中，藉 `using` 指示詞將 `concurrency` 命名空間加入。  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  
4.  在 `CChildView::DrawMandelbrot` 方法中，在呼叫 `Bitmap::UnlockBits` 之後呼叫 [concurrency::send](../Topic/send%20Function.md) 函式，將 `Bitmap` 物件傳遞至 UI 執行緒。  然後，張貼一則繪製訊息到 UI 執行緒，並將用戶端區域設定為無效。  
  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  更新 `CChildView::OnPaint` 方法，以接收更新後的 `Bitmap` 物件並將影像繪製到用戶端視窗。  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     如果訊息緩衝區中沒有用來產生 Mandelbrot 影像的工作，則 `CChildView::OnPaint` 方法會建立該項工作。  像是在初始繪製訊息或是當另一個視窗移到用戶端視窗之前的情況下，訊息緩衝區就不會包含 `Bitmap` 物件。  
  
6.  建置並執行應用程式，藉以確認應用程式更新成功。  
  
 因為繪製工作是在背景執行，所以現在 UI 的反應更加靈敏。  
  
 \[[上方](#top)\]  
  
##  <a name="performance"></a> 提升繪製效能  
 Mandelbrot 碎形的產生相當適用於平行化作業，因為每一個像素的計算作業獨立於其他所有計算作業之外。  若要平行處理繪製程序，請將 `CChildView::DrawMandelbrot` 方法中的外部 `for` 迴圈轉換為對 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法的呼叫，如下所示。  
  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 因為每一個點陣圖項目的計算作業都是獨立的，所以您不必同步處理存取點陣圖記憶體的繪製作業。  如此一來，效能即可隨著可用的處理器數目增加而提升。  
  
 \[[上方](#top)\]  
  
##  <a name="cancellation"></a> 加入取消的支援  
 本節說明如何處理視窗大小的調整，以及如何在視窗終結時取消任何作用中的繪製工作。  
  
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md) 這份文件說明在執行階段中取消 \(Cancellation\) 是如何的運作。   取消作業是合作式作業；因此，並不會立即發生。  為了要停止已取消的工作，執行階段會在該工作對執行階段的後續呼叫中擲回一個內部例外狀況。  上一節顯示如何使用 `parallel_for` 演算法來改善繪製工作的效能。  呼叫 `parallel_for` 可讓執行階段停止工作，並因而讓取消作業發生作用。  
  
### 取消作用中的工作  
 Mandelbrot 應用程式會建立其維度與用戶端視窗大小相符的 `Bitmap` 物件。  每次調整用戶端視窗大小時，應用程式就會建立額外的背景工作，以便產生符合新視窗大小的影像。  應用程式並不需要這些中繼影像，而只需要最終視窗大小的影像。  若要防止應用程式執行這項額外的工作，您可以在 `WM_SIZE` 和 `WM_SIZING` 訊息的訊息處理常式中取消任何作用中的繪製工作，然後在視窗大小調整之後重新排程繪製工作。  
  
 為了在調整視窗大小時取消作用中的繪製工作，應用程式會在 `WM_SIZING` 和 `WM_SIZE` 訊息的處理常式中呼叫 [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) 方法。  `WM_SIZE` 訊息的處理常式也會呼叫 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md) 方法，等待所有作用中的工作完成，然後針對更新後的視窗大小重新排程繪製工作。  
  
 當用戶端視窗終結後，取消任何作用中的繪製工作是很好的作法。  取消任何作用中的繪製工作可確保背景工作執行緒不會在用戶端視窗終結後，將訊息張貼到 UI 執行緒。  應用程式會在 `WM_DESTROY` 訊息的處理常式中取消任何作用中的繪製工作。  
  
### 回應取消作業  
 執行繪製工作的 `CChildView::DrawMandelbrot` 方法必須回應取消作業。  因為執行階段使用例外處理來取消工作，所以 `CChildView::DrawMandelbrot` 方法必須使用可安全處理所有例外狀況的機制來保證所有資源都已正確清除。  本範例使用「*資源擷取為初始設定*」\(Resource Acquisition Is Initialization，RAII\) 模式來保證點陣圖位元會在取消工作後解除鎖定。  
  
##### 若要在 Mandelbrot 應用程式中加入取消作業的支援  
  
1.  在 ChildView.h 中，於 `CChildView` 類別的 `protected` 區段中，加入 `OnSize`、`OnSizing` 和 `OnDestroy` 訊息對應函式的宣告。  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  在 ChildView.cpp 中，修改訊息對應以包含 `WM_SIZE`、`WM_SIZING` 和 `WM_DESTROY` 訊息的處理常式。  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  實作 `CChildView::OnSizing` 方法。  這個方法會取消任何現有的繪製工作。  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  實作 `CChildView::OnSize` 方法。  這個方法會取消任何現有的繪製工作，並針對更新後的用戶端視窗大小建立新的繪製工作。  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  實作 `CChildView::OnDestroy` 方法。  這個方法會取消任何現有的繪製工作。  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  在 ChildView.cpp 中，定義 `scope_guard` 類別，以實作 RAII 模式。  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  在呼叫 `Bitmap::LockBits` 之後，將下列程式碼加入至 `CChildView::DrawMandelbrot` 方法：  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     此程式碼會建立 `scope_guard` 物件，進而處理取消作業。  當此物件脫離範圍時，便會將點陣圖位元解除鎖定。  
  
8.  修改 `CChildView::DrawMandelbrot` 方法的尾端，以便在點陣圖位元解除鎖定之後解除 `scope_guard` 物件，但是在任何訊息傳送至 UI 執行緒之前。  這可確保 UI 執行緒不會在點陣圖位元解除鎖定之前進行更新。  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. 建置並執行應用程式，藉以確認應用程式更新成功。  
  
 當您調整視窗大小時，只會針對最終視窗大小執行繪製工作。  所有作用中的繪製工作也會在視窗終結後取消。  
  
 \[[上方](#top)\]  
  
## 請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [MFC 桌面應用程式](../../mfc/mfc-desktop-applications.md)