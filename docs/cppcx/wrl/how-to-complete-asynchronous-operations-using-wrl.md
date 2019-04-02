---
title: HOW TO：使用 WRL 完成非同步作業
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 321bb273f661ec16fe85443c449b425ae56b99e3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784565"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>HOW TO：使用 WRL 完成非同步作業

本文件說明如何使用 Windows 執行階段 c + + 範本庫 (WRL) 來啟動非同步作業，並在作業完成時執行工作。

本文件說明兩個範例。 第一個範例會啟動非同步的計時器，並等候計時器過期。 在此範例中，您會指定非同步的動作，當您建立計時器物件。 第二個範例會執行背景工作執行緒。 此範例示範如何使用 Windows 執行階段方法會傳回`IAsyncInfo`介面。 [回呼](callback-function-wrl.md)函式是這兩個範例中很重要的一部分，因為它可讓它們指定事件處理常式來處理非同步作業的結果。

如需更基本範例會建立元件的執行個體，並擷取屬性值，請參閱[How to:啟動與使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。

> [!TIP]
> 這些範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件 (functor)，函式指標，或是[std:: function](../../standard-library/function-class.md)物件。 如需有關 c + + lambda 運算式的詳細資訊，請參閱[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

## <a name="example-working-with-a-timer"></a>範例：與計時器工作

下列步驟啟動非同步的計時器，並等候計時器過期。 完整的範例如下。

> [!WARNING]
> 雖然您通常會使用 Windows 執行階段 c + + 樣板程式庫，在通用 Windows 平台 (UWP) 應用程式中，此範例會使用主控台應用程式的圖。 這類函式`wprintf_s`所沒有的 UWP 應用程式。 如需類型和您可以使用 UWP 應用程式中的函式的詳細資訊，請參閱[通用 Windows 平台應用程式不支援的 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)並[Win32 與 UWP 應用程式的 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

1. 包含 (`#include`) 任何所需的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` 宣告的類型，才能使用非同步的計時器。

   建議您利用`using namespace`在.cpp 檔案中，讓程式碼更容易閱讀的指示詞。

2. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. 建立啟用 factory`ABI::Windows::System::Threading::IThreadPoolTimer`介面。

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Windows 執行階段會使用完整名稱來識別類型。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`參數是由 Windows 執行階段，並包含必要的執行階段類別名稱的字串。

4. 建立[事件](event-class-wrl.md)計時器回撥至主應用程式會同步處理的物件。

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > 這個事件是針對只為一部分的主控台應用程式的示範。 此範例會使用事件來確保應用程式結束之前會完成非同步作業。 在大部分的應用程式，您通常不等待非同步作業完成。

5. 建立`IThreadPoolTimer`兩秒之後到期的物件。 使用`Callback`函式來建立事件處理常式 (`ABI::Windows::System::Threading::ITimerElapsedHandler`物件)。

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. 將訊息列印至主控台，並等候完成的計時器回呼。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`wrl-consume-async.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>範例：使用背景執行緒

下列步驟啟動背景工作執行緒，並定義該執行緒所執行的動作。 完整的範例如下。

> [!TIP]
> 此範例示範如何使用`ABI::Windows::Foundation::IAsyncAction`介面。 您可以將此模式套用至任何實作的介面`IAsyncInfo`: `IAsyncAction`， `IAsyncActionWithProgress`， `IAsyncOperation`，和`IAsyncOperationWithProgress`。

1. 包含 (`#include`) 任何所需的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h 宣告將背景工作執行緒所需的類型。

   我們建議您改用`using namespace`在.cpp 檔案中，讓程式碼更容易閱讀的指示詞。

2. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. 建立啟用 factory`ABI::Windows::System::Threading::IThreadPoolStatics`介面。

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. 建立[事件](event-class-wrl.md)同步處理至主應用程式的背景工作執行緒完成的物件。

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > 這個事件是針對只為一部分的主控台應用程式的示範。 此範例會使用事件來確保應用程式結束之前會完成非同步作業。 在大部分的應用程式，您通常不等待非同步作業完成。

5. 呼叫`IThreadPoolStatics::RunAsync`方法用來建立背景工作執行緒。 使用`Callback`函式來定義的動作。

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime`函式定義於接下來的完整範例。

6. 將訊息列印至主控台，並等候完成執行緒。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`wrl-consume-asyncOp.cpp`，然後執行下列命令中**Visual Studio 命令提示字元**視窗。

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)