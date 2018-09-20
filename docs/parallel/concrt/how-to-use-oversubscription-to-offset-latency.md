---
title: 如何： 使用過度訂閱位移延遲 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f96a8a27b511c1a93114c32d048043aa9562fe1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392956"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用過度訂閱使延遲產生位移

過度訂閱可以改善整體的某些應用程式包含具有大量延遲的工作效率。 本主題說明如何使用過度訂閱位移從網路連線讀取資料所造成的延遲。

## <a name="example"></a>範例

這個範例會使用[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)從 HTTP 伺服器下載檔案。 `http_reader`類別衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)並且使用訊息傳遞，以非同步方式讀取要下載的 URL 名稱。

`http_reader`類別會使用[concurrency:: task_group](reference/task-group-class.md)以並行方式讀取每個檔案的類別。 每個工作會呼叫[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法`_BeginOversubscription`參數設定為`true`啟用過度訂閱目前內容中的。 每個工作，然後使用 Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md)並[CHttpFile](../../mfc/reference/chttpfile-class.md)類別來下載檔案。 最後，每個工作會呼叫`Context::Oversubscribe`具有`_BeginOversubscription`參數設為`false`停用過度訂閱。

啟用過度訂閱時，執行階段會建立一個額外的執行緒，在其中執行工作。 每個執行緒可以也過度訂閱目前內容，並藉此建立額外的執行緒。 `http_reader`類別會使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)物件來限制應用程式使用的執行緒數目。 代理程式初始化緩衝區中，使用固定數目的語彙基元值。 每個下載作業，代理程式會從緩衝區讀取語彙基元的值之前作業啟動，然後將該值傳回寫入的緩衝區在作業完成之後。 當緩衝區是空的時代理程式等候其中一個值回寫入緩衝區的下載作業。

下列範例會限制同時以兩倍的可用硬體執行緒數目的工作數目。 這個值會是不錯的起點使用當您試驗過度訂閱。 您可以使用符合特定的處理環境的值，或以動態方式變更此值以回應實際的工作負載。

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

此範例會產生具有四個處理器的電腦上的下列輸出：

```Output
Downloading http://www.adatum.com/...
Downloading http://www.adventure-works.com/...
Downloading http://www.alpineskihouse.com/...
Downloading http://www.cpandl.com/...
Downloading http://www.cohovineyard.com/...
Downloading http://www.cohowinery.com/...
Downloading http://www.cohovineyardandwinery.com/...
Downloading http://www.contoso.com/...
Downloading http://www.consolidatedmessenger.com/...
Downloading http://www.fabrikam.com/...
Downloading http://www.fourthcoffee.com/...
Downloading http://www.graphicdesigninstitute.com/...
Downloading http://www.humongousinsurance.com/...
Downloading http://www.litwareinc.com/...
Downloading http://www.lucernepublishing.com/...
Downloading http://www.margiestravel.com/...
Downloading http://www.northwindtraders.com/...
Downloading http://www.proseware.com/...
Downloading http://www.fineartschool.net...
Downloading http://www.tailspintoys.com/...
Downloaded 1801040 bytes in 3276 ms.
```

因為其他工作執行其他工作在等候潛伏的作業完成時，啟用過度訂閱時，可以更快執行此範例。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`download-oversubscription.cpp`和執行的下列其中之一然後命令在 Visual Studio 命令提示字元 視窗中。

**cl.exe /EHsc /MD /D"_AFXDLL"download-oversubscription.cpp**

**cl.exe /EHsc /MT download-oversubscription.cpp**

## <a name="robust-programming"></a>穩固程式設計

永遠停用過度訂閱之後您不再需要它。 請考慮不會處理另一個函式所擲回例外狀況的函式。 如果函式傳回之前未停用過度訂閱，任何額外的平行工作也會過度訂閱目前的內容。

您可以使用*資源擷取即初始化*(RAII) 模式，可限制在指定的範圍內的過度訂閱。 RAII 模式下的資料結構是在堆疊上配置。 該資料結構初始化，或建立和終結或終結的資料結構時釋放該資源時，取得資源。 RAII 模式可保證，封閉範圍結束之前，會呼叫解構函式。 因此，資源受到妥善管理擲回例外狀況時，或函式包含多個`return`陳述式。

下列範例會定義名為結構`scoped_blocking_signal`。 建構函式`scoped_blocking_signal`結構啟用過度訂閱和解構函式停用過度訂閱。

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

下列範例會修改主體`download`函式傳回之前，已停用，用以確保過度訂閱的 RAII 的方法。 這項技術可確保`download`方法是例外狀況安全的。

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>另請參閱

[內容](../../parallel/concrt/contexts.md)<br/>
[Context:: oversubscribe 方法](reference/context-class.md#oversubscribe)

