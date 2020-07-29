---
title: 如何：使用過度訂閱使延遲產生位移
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: f5d48b68d03adc25cd5f87122591b52e37da700a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219595"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用過度訂閱使延遲產生位移

超額訂閱可以改善某些應用程式的整體效率，其中包含具有大量延遲的工作。 本主題說明如何使用超額訂閱來抵銷從網路連線讀取資料所造成的延遲。

## <a name="example"></a>範例

這個範例會使用[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫，從 HTTP 伺服器下載檔案。 `http_reader`類別衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md) ，並使用訊息傳遞以非同步方式讀取要下載的 URL 名稱。

`http_reader`類別會使用[concurrency：： task_group](reference/task-group-class.md)類別，同時讀取每個檔案。 每個工作都會呼叫[concurrency：： CoNtext：：超額](reference/context-class.md#oversubscribe)方法，並將 `_BeginOversubscription` 參數設定為， **`true`** 以在目前的內容中啟用過度訂閱。 然後，每個工作都會使用 Microsoft Foundation class （MFC） [CInternetSession](../../mfc/reference/cinternetsession-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md)類別來下載檔案。 最後，每個工作都會呼叫， `Context::Oversubscribe` 並將 `_BeginOversubscription` 參數設定為， **`false`** 以停用過度訂閱。

當過度訂閱啟用時，執行時間會建立一個額外的執行緒來執行工作。 這些執行緒中的每個都可能也會過度訂閱目前的內容，因此會建立額外的執行緒。 `http_reader`類別會使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)物件來限制應用程式所使用的執行緒數目。 代理程式會使用固定數目的 token 值來初始化緩衝區。 針對每個下載作業，代理程式會在作業開始之前從緩衝區讀取 token 值，然後在作業完成之後將該值寫入緩衝區。 當緩衝區是空的時，代理程式會等候其中一個下載作業將值寫回緩衝區。

下列範例會將同時工作的數目限制為可用硬體執行緒數目的兩倍。 當您嘗試超額訂閱時，這個值是不錯的起點。 您可以使用符合特定處理環境的值，或動態變更此值以回應實際的工作負載。

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

這個範例會在具有四個處理器的電腦上產生下列輸出：

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

啟用過度訂閱時，此範例的執行速度會更快，因為其他工作會執行其他工作，而其他工作則會等候潛在的作業完成。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `download-oversubscription.cpp` 然後在 [ **Visual Studio 命令提示**字元] 視窗中執行下列其中一個命令。

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>穩固程式設計

當您不再需要超額訂閱之後，請一律停用。 假設有一個函式不會處理另一個函數所擲回的例外狀況。 如果您未在函式傳回之前停用過度訂閱，則任何額外的平行工作也會過度訂閱目前的內容。

您可以使用*資源取得為初始化*（RAII）模式，將超額訂閱限制為指定的範圍。 在 RAII 模式下，會在堆疊上配置資料結構。 該資料結構會在建立時初始化或取得資源，並在終結資料結構時，終結或釋放該資源。 RAII 模式可保證在封閉範圍結束之前呼叫此析構函式。 因此，當擲回例外狀況時，或當函數包含多個語句時，會正確地管理資源 **`return`** 。

下列範例會定義名為的結構 `scoped_blocking_signal` 。 結構的函式會 `scoped_blocking_signal` 啟用過度訂閱，而此析構函數會停用超額訂閱。

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

下列範例會將方法的主體修改 `download` 為使用 RAII，以確保在函式傳回之前已停用過度訂閱。 這項技術可確保 `download` 方法是例外狀況安全的。

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>另請參閱

[內容](../../parallel/concrt/contexts.md)<br/>
[Context::Oversubscribe 方法](reference/context-class.md#oversubscribe)
