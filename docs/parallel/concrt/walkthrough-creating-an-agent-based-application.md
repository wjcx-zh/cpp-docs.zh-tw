---
title: 逐步解說：建立代理程式架構應用程式
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 3ece04811a75fba22db447875dc6ed08c22987b5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142046"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>逐步解說：建立代理程式架構應用程式

本主題說明如何建立以代理程式為基礎的基本應用程式。 在此逐步解說中，您可以建立代理程式，以非同步方式從文字檔讀取資料。 應用程式會使用 Adler-32 總和檢查碼演算法來計算該檔案內容的總和檢查碼。

## <a name="prerequisites"></a>必要條件

您必須瞭解下列主題，才能完成此逐步解說：

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)

- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a> 章節

本逐步解說示範如何執行下列工作：

- [建立主控台應用程式](#createapplication)

- [建立 file_reader 類別](#createagentclass)

- [在應用程式中使用 file_reader 類別](#useagentclass)

## <a name="createapplication"></a>建立主控台應用程式

本節說明如何建立C++主控台應用程式，以參考程式將使用的標頭檔。 初始步驟會根據您使用的 Visual Studio 版本而有所不同。 請確定已在此頁面的左上方正確設定版本選取器。

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>在 Visual Studio 2019 C++中建立主控台應用程式

1. 從主功能表中 **，選擇 [** 檔案] > [**新增**>**專案**]，開啟 [**建立新的專案**] 對話方塊。

1. 在對話方塊頂端，將 [語言] 設定為 **C++** ，將 [平台] 設定為 **Windows**，並將 [專案類型] 設定為**主控台**。 

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]，然後選擇 [下一步]。 在下一個頁面中，輸入 `BasicAgent` 做為專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] 按鈕以建立專案。

1. 以滑鼠右鍵按一下**方案總管**中的專案節點，然後選擇 [**屬性**]。 在 [設定**屬性**] > **CC++ /**  > 先行**編譯頭**檔 > 先行**編譯頭**檔選擇 [**建立**]。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>在 Visual Studio 2017 C++和更早版本中建立主控台應用程式

1. 在 [**檔案**] 功能表上，按一下 [**新增**]，然後按一下 [**專案**] 以顯示 [**新增專案**] 對話方塊。

1. 在 [**新增專案**] 對話方塊中，選取 [**專案類型**] 窗格中的**視覺效果C++** 節點，然後在 [**範本**] 窗格中選取 [ **Win32 主控台應用程式**]。 輸入專案的名稱，例如 `BasicAgent`，然後按一下 **[確定]** 以顯示 [ **Win32 主控台應用程式]** 。

1. 在 [ **Win32 主控台應用程式精靈**] 對話方塊中，按一下 **[完成]** 。

::: moniker-end

1. 在*pch* （Visual Studio 2017 和更早版本的*stdafx.h* ）中，新增下列程式碼：

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   標頭檔代理程式. h 包含[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)類別的功能。

1. 藉由建立並執行應用程式，確認已成功建立。 若要建立應用程式，請在 [**建立**] 功能表上，按一下 [**建立方案**]。 如果成功建立應用程式，請按一下 [**調試**程式] 功能表上的 [**啟動調試**程式] 來執行應用程式。

[[靠上](#top)]

## <a name="createagentclass"></a>建立 file_reader 類別

本節說明如何建立 `file_reader` 類別。 執行時間會排程每個代理程式，以在其本身的內容中執行工作。 因此，您可以建立可同步執行工作的代理程式，但會以非同步方式與其他元件互動。 `file_reader` 類別會從指定的輸入檔讀取資料，並將資料從該檔案傳送到指定的目標群組件。

#### <a name="to-create-the-file_reader-class"></a>若要建立 file_reader 類別

1. 將新的C++標頭檔新增至您的專案。 若要這樣做，請在**方案總管**中的 [**標頭檔**] 節點上按一下滑鼠右鍵，按一下 [**加入**]，然後按一下 [**新增專案**]。 在 [**範本**] 窗格中，選取 [**標頭檔（.h）** ]。 在 [**加入新專案**] 對話方塊的 [**名稱**] 方塊中，輸入 `file_reader.h`，然後按一下 [**新增**]。

1. 在 file_reader .h 中，加入下列程式碼。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. 在 file_reader 中，建立一個衍生自 `agent`的類別，名為 `file_reader`。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. 將下列資料成員新增至類別的 `private` 區段。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name` 成員是代理程式讀取來源的檔案名。 `_target` 成員是 agent 將檔案內容寫入的[concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md)物件。 `_error` 成員會保存代理程式生命週期期間所發生的任何錯誤。

1. 將下列 `file_reader` 的程式碼加入至 `file_reader` 類別的 `public` 區段。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   每個函式多載都會設定 `file_reader` 的資料成員。 第二個和第三個函式多載可讓您的應用程式使用特定排程器搭配您的代理程式。 第一個多載會將預設排程器與您的代理程式搭配使用。

1. 將 `get_error` 方法加入至 `file_reader` 類別的 public 區段。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error` 方法會抓取代理程式生命週期期間所發生的任何錯誤。

1. 在類別的 `protected` 區段中，執行[concurrency：： agent：： run](reference/agent-class.md#run)方法。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run` 方法會開啟檔案，並從該檔案讀取資料。 `run` 方法會使用例外狀況處理來捕捉檔案處理期間所發生的任何錯誤。

   每次此方法從檔案讀取資料時，它會呼叫[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函式，將該資料傳送至目標緩衝區。 它會將空字串傳送至其目標緩衝區，以指出處理結束。

下列範例會顯示 file_reader 的完整內容。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[靠上](#top)]

## <a name="useagentclass"></a>在應用程式中使用 file_reader 類別

本節說明如何使用 `file_reader` 類別來讀取文字檔的內容。 它也會示範如何建立可接收此檔案資料並計算其 Adler-32 總和檢查碼的[concurrency：： call](../../parallel/concrt/reference/call-class.md)物件。

#### <a name="to-use-the-file_reader-class-in-your-application"></a>在您的應用程式中使用 file_reader 類別

1. 在 BasicAgent 中，新增下列 `#include` 語句。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. 在 BasicAgent 中，新增下列 `using` 指示詞。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. 在 `_tmain` 函式中，建立會發出信號結束處理的[concurrency：： event](../../parallel/concrt/reference/event-class.md)物件。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. 建立 `call` 物件，以在收到資料時更新總和檢查碼。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   這個 `call` 物件也會在收到空字串以通知處理結束時，設定 `event` 物件。

1. 建立從檔案 test.txt 讀取的 `file_reader` 物件，並將該檔案的內容寫入 `call` 物件。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. 啟動代理程式，並等候它完成。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. 等候 `call` 物件接收所有資料並完成。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. 檢查檔案讀取器是否有錯誤。 如果未發生任何錯誤，請計算最終的 Adler-32 總和，並將總和列印到主控台。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

下列範例會顯示完整的 BasicAgent .cpp 檔案。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[靠上](#top)]

## <a name="sample-input"></a>範例輸入

這是輸入檔 text .txt 的範例內容：

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>取樣輸出

搭配範例輸入使用時，此程式會產生下列輸出：

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>最佳化程式設計

若要防止平行存取資料成員，建議您將執行工作的方法新增至類別的 `protected` 或 `private` 區段。 只會將傳送或接收訊息的方法加入至您類別的 `public` 區段。

一律呼叫[concurrency：： agent：:d 一種](reference/agent-class.md#done)方法，將代理程式移至已完成狀態。 您通常會先呼叫這個方法，然後再從 `run` 方法返回。

## <a name="next-steps"></a>後續步驟

如需以代理程式為基礎的另一個範例，請參閱[逐步解說：使用聯結以避免鎖死](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)<br/>
[逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
