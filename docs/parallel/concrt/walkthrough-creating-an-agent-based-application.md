---
title: 逐步解說：建立代理程式為基礎的應用程式
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: c249bc8138a3617cce3eae836751575b2626f4aa
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857318"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>逐步解說：建立代理程式為基礎的應用程式

本主題描述如何建立基本的代理程式型應用程式。 在本逐步解說中，您可以建立以非同步方式從文字檔讀取資料的代理程式。 應用程式會使用 Adler-32 總和檢查碼演算法來計算總和檢查碼，該檔案的內容。

## <a name="prerequisites"></a>必要條件

您必須了解下列主題，以完成此逐步解說：

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> 章節

本逐步解說示範如何執行下列工作：

- [建立主控台應用程式](#createapplication)

- [建立 file_reader 類別](#createagentclass)

- [在 應用程式中使用 file_reader 類別](#useagentclass)

##  <a name="createapplication"></a> 建立主控台應用程式

本節說明如何建立C++主控台應用程式所參考的程式將使用的標頭檔。 初始步驟需視您所使用的 Visual Studio 版本而有所不同。 請確定版本選擇器已正確設定，此頁面的左上角。

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>若要建立C++主控台應用程式在 Visual Studio 2019

1. 從主功能表中，選擇**檔案** > **新增** > **專案**開啟**建立新的專案**對話方塊方塊。

1. 在對話方塊頂端，設定**語言**來**C++**，將**平台**至**Windows**，並將**專案類型**要**主控台**。 

1. 從 [專案類型的篩選清單，選擇**主控台應用程式**然後選擇**下一步]**。 在下一步 頁面中，輸入`BasicAgent`做為專案的名稱，並指定專案位置，如有需要。

1. 選擇**建立**按鈕，以建立專案。

1. 中的專案節點上按一下滑鼠右鍵**方案總管**，然後選擇**屬性**。 底下**組態屬性** > **C /C++** > **先行編譯標頭** > **先行編譯標頭**選擇 **建立**。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>若要建立C++主控台應用程式在 Visual Studio 2017 及更早版本

1. 上**檔案**功能表上，按一下**新增**，然後按一下 [**專案**以顯示**新專案**] 對話方塊。

1. 在 **新的專案**對話方塊中，選取**Visual C++** 中的節點**專案類型**窗格，然後選取**Win32 主控台應用程式**中**範本**窗格。 輸入專案名稱，例如`BasicAgent`，然後按一下 **[確定]** 以顯示**Win32 主控台應用程式精靈**。

1. 在 [ **Win32 主控台應用程式精靈**] 對話方塊中，按一下**完成**。

::: moniker-end

1. 在 stdafx.h （或 Visual studio 版本而定的 pch.h），加入下列程式碼。

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   標頭檔 agents.h 包含的功能[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)類別。

1. 請確認應用程式已成功建立，建置並執行它。 若要在建置應用程式時，**建置**功能表上，按一下**建置方案**。 如果應用程式建置成功，請按一下 執行應用程式**開始偵錯**上**偵錯**功能表。

[[靠上](#top)]

##  <a name="createagentclass"></a> 建立 file_reader 類別

本節說明如何建立`file_reader`類別。 執行階段排程是在自己的內容中執行工作的每個代理程式。 因此，您可以建立代理程式，以同步方式執行工作，但以非同步方式與其他元件互動。 `file_reader`類別會從指定的輸入檔讀取資料，並將資料從該檔案傳送至指定的目標元件。

#### <a name="to-create-the-filereader-class"></a>若要建立 file_reader 類別

1. 新增C++標頭檔案加入專案。 若要這樣做，請以滑鼠右鍵按一下**標頭檔**中的節點**方案總管**，按一下**新增**，然後按一下**新項目**。 在 **範本**窗格中，選取**標頭檔 (.h)**。 在 [**加入新項目**] 對話方塊中，輸入`file_reader.h`中**名稱**方塊，然後按一下**新增**。

1. 在 file_reader.h，加入下列程式碼。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. 在 file_reader.h，建立名為類別`file_reader`衍生自`agent`。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. 將下列資料成員加入`private`類別的一節。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name`成員是代理程式讀取的檔案名稱。 `_target`成員[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)物件代理程式寫入至檔案的內容。 `_error`成員包含代理程式的生命期限內，就會發生任何錯誤。

1. 新增下列程式碼`file_reader`建構函式`public`一節`file_reader`類別。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   每個建構函式多載設定`file_reader`資料成員。 第二個和第三個建構函式多載可讓您的應用程式，以搭配您的代理程式的特定排程器。 第一個多載會使用您的代理程式的預設排程器。

1. 新增`get_error`方法的 public 區段`file_reader`類別。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error`方法會擷取代理程式的生命期限內，就會發生任何錯誤。

1. 實作[2&gt;concurrency::agent::run&lt;2}](reference/agent-class.md#run)方法中的`protected`類別的一節。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run`方法開啟檔案，並從中讀取資料。 `run`方法會使用例外狀況處理來擷取檔案處理期間發生任何錯誤。

   它會呼叫這個方法會將資料讀取檔案，每次[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式，將該資料傳送至目標緩衝區。 它會空的字串傳送至其目標的緩衝區，表示處理結束時。

下列範例顯示 file_reader.h 的完整內容。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[靠上](#top)]

##  <a name="useagentclass"></a> 在 應用程式中使用 file_reader 類別

本節說明如何使用`file_reader`類別來讀取文字檔的內容。 它也會示範如何建立[concurrency:: call](../../parallel/concrt/reference/call-class.md)接收這個檔案資料，並計算其 Adler-32 總和檢查碼的物件。

#### <a name="to-use-the-filereader-class-in-your-application"></a>若要在您的應用程式中使用 file_reader 類別

1. 在 BasicAgent.cpp，新增下列`#include`陳述式。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. 在 BasicAgent.cpp，新增下列`using`指示詞。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. 在 `_tmain`函式中，建立[concurrency:: event](../../parallel/concrt/reference/event-class.md)訊號處理結束的物件。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. 建立`call`接收資料時，更新總和檢查碼的物件。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   這`call`物件也會設定`event`物件收到空的字串，以表示處理結束時。

1. 建立`file_reader`檢閱 test.txt 檔案讀取和寫入至該檔案的內容物件`call`物件。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. 啟動代理程式，並等候它完成。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. 等候`call`接收所有資料，並完成的物件。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. 請檢查錯誤的檔案讀取器。 如果不發生任何錯誤，計算最終的 Adler-32 總和，並列印到主控台的總和。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

下列範例示範完整的 BasicAgent.cpp 檔案。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[靠上](#top)]

## <a name="sample-input"></a>範例輸入

這是範例輸入的檔 text.txt 內容：

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>範例輸出

輸入範例搭配使用時，此程式會產生下列輸出：

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>穩固程式設計

若要防止資料成員的並行存取，我們建議您將新增方法執行的工作來`protected`或`private`類別的一節。 只有加入 傳送或接收訊息，或從代理程式的方法`public`類別的一節。

請務必呼叫[concurrency:: agent:: 完成](reference/agent-class.md#done)方法來移動您的代理程式已完成的狀態。 一般都會呼叫這個方法之前，您從傳回`run`方法。

## <a name="next-steps"></a>後續步驟

如需代理程式為基礎的應用程式的其他範例，請參閱[逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)<br/>
[逐步解說：使用聯結以預防死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
