---
title: 如何：使用 WRL 完成非同步作業
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 8e7e52342cf73a56c6c33d4d1f998f446d632ddd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213937"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>如何：使用 WRL 完成非同步作業

本檔說明如何使用 Windows 執行階段C++範本庫（WRL）來啟動非同步作業，並在作業完成時執行工作。

本檔說明兩個範例。 第一個範例會啟動非同步計時器，並等候計時器過期。 在此範例中，您會在建立 timer 物件時指定非同步動作。 第二個範例會執行背景工作執行緒。 這個範例示範如何使用會傳回 `IAsyncInfo` 介面的 Windows 執行階段方法。 [回檔](callback-function-wrl.md)函數是這兩個範例的重要部分，因為它可讓它們指定事件處理常式來處理非同步作業的結果。

如需建立元件實例並抓取屬性值的更基本範例，請參閱[如何：啟用和使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。

> [!TIP]
> 這些範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件（函子）、函數指標或[std：： function](../../standard-library/function-class.md)物件。 如需C++ lambda 運算式的詳細資訊，請參閱[lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

## <a name="example-working-with-a-timer"></a>範例：使用計時器

下列步驟會啟動非同步計時器，並等候計時器過期。 完整的範例如下所示。

> [!WARNING]
> 雖然您通常會在通用 Windows 平臺C++ （UWP）應用程式中使用 Windows 執行階段範本庫，但此範例會使用主控台應用程式來進行說明。 UWP 應用程式無法使用如 `wprintf_s` 之類的功能。 如需有關可在 UWP 應用程式中使用之類型和函式的詳細資訊，請參閱[通用 Windows 平臺應用程式中不支援的 CRT](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)函式和[適用于 uwp 應用程式的 Win32 和 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

1. 包含（`#include`）任何必要的 Windows 執行階段、 C++ Windows 執行階段範本程式庫C++或標準程式庫標頭。

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` 宣告使用非同步計時器所需的類型。

   我們建議您利用 .cpp 檔案中的 `using namespace` 指示詞，讓程式碼更容易閱讀。

2. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. 建立 `ABI::Windows::System::Threading::IThreadPoolTimer` 介面的啟用 factory。

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Windows 執行階段使用完整名稱來識別類型。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` 參數是由 Windows 執行階段提供的字串，其中包含所需的執行時間類別名稱。

4. 建立[事件](event-class-wrl.md)物件，以將計時器回呼同步處理至主應用程式。

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > 此事件僅供示範做為主控台應用程式的一部分。 這個範例會使用事件，以確保非同步作業會在應用程式結束之前完成。 在大部分的應用程式中，您通常不會等候非同步作業完成。

5. 建立在兩秒後過期的 `IThreadPoolTimer` 物件。 使用 `Callback` 函數來建立事件處理常式（`ABI::Windows::System::Threading::ITimerElapsedHandler` 物件）。

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. 將訊息列印至主控台，並等候計時器回呼完成。 所有 `ComPtr` 和 RAII 物件都會離開範圍，並自動釋放。

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `wrl-consume-async.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>範例：使用背景執行緒

下列步驟會啟動背景工作執行緒，並定義該執行緒所執行的動作。 完整的範例如下所示。

> [!TIP]
> 這個範例示範如何使用 `ABI::Windows::Foundation::IAsyncAction` 介面。 您可以將此模式套用至任何會執行 `IAsyncInfo`： `IAsyncAction`、`IAsyncActionWithProgress`、`IAsyncOperation`和 `IAsyncOperationWithProgress`的介面。

1. 包含（`#include`）任何必要的 Windows 執行階段、 C++ Windows 執行階段範本程式庫C++或標準程式庫標頭。

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows System.object 會宣告使用背景工作執行緒所需的類型。

   我們建議您在 .cpp 檔案中使用 `using namespace` 指示詞，讓程式碼更容易閱讀。

2. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. 建立 `ABI::Windows::System::Threading::IThreadPoolStatics` 介面的啟用 factory。

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. 建立[事件](event-class-wrl.md)物件，以將背景工作執行緒的完成同步處理到主應用程式。

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > 此事件僅供示範做為主控台應用程式的一部分。 這個範例會使用事件，以確保非同步作業會在應用程式結束之前完成。 在大部分的應用程式中，您通常不會等候非同步作業完成。

5. 呼叫 `IThreadPoolStatics::RunAsync` 方法，以建立背景工作執行緒。 使用 `Callback` 函數來定義動作。

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   在接下來的完整範例中，會定義 `IsPrime` 函數。

6. 將訊息列印至主控台，並等候執行緒完成。 所有 `ComPtr` 和 RAII 物件都會離開範圍，並自動釋放。

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `wrl-consume-asyncOp.cpp` 的檔案中，然後在 [ **Visual Studio 命令提示**字元] 視窗中執行下列命令。

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)
