---
title: 如何：使用 WRL 處理事件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 0e13212d7cb481bc72a903a31fb170fd1ff8b7ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213924"
---
# <a name="how-to-handle-events-using-wrl"></a>如何：使用 WRL 處理事件

本檔說明如何使用 Windows 執行階段C++範本庫（WRL）來訂閱和處理 Windows 執行階段物件的事件。

如需建立該元件的實例並抓取屬性值的更基本範例，請參閱[如何：啟用和使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。

## <a name="subscribing-to-and-handling-events"></a>訂閱和處理事件

下列步驟會啟動 `ABI::Windows::System::Threading::IDeviceWatcher` 物件，並使用事件處理常式來監視進度。 `IDeviceWatcher` 介面可讓您在新增、移除或變更裝置時，以非同步方式或在背景中列舉裝置，並接收通知。 [回檔](callback-function-wrl.md)函式是此範例中很重要的一部分，因為它可讓它指定處理背景作業結果的事件處理常式。 完整的範例如下所示。

> [!WARNING]
> 雖然您通常會在通用 Windows 平臺C++應用程式中使用 Windows 執行階段範本庫，但此範例會使用主控台應用程式來進行說明。 通用 Windows 平臺應用程式無法使用如 `wprintf_s` 之類的功能。 如需您可以在通用 Windows 平臺應用程式中使用之類型和函式的詳細資訊，請參閱[通用 Windows 平臺應用程式中不支援的 CRT](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)函式和[適用于 UWP 應用程式的 Win32 和 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

1. 包含（`#include`）任何必要的 Windows 執行階段、 C++ Windows 執行階段範本程式庫C++或標準程式庫標頭。

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` 宣告列舉裝置所需的類型。

   我們建議您利用 .cpp 檔案中的 `using namespace` 指示詞，讓程式碼更容易閱讀。

2. 宣告應用程式的本機變數。 這個範例會保留列舉裝置的數目，以及可讓它在稍後取消訂閱事件的註冊權杖計數。

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. 建立[事件](event-class-wrl.md)物件，以將列舉程式的完成同步處理到主要應用程式。

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > 此事件僅供示範做為主控台應用程式的一部分。 這個範例會使用事件，以確保非同步作業會在應用程式結束之前完成。 在大部分的應用程式中，您通常不會等候非同步作業完成。

5. 建立 `IDeviceWatcher` 介面的啟用 factory。

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Windows 執行階段使用完整名稱來識別類型。 `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` 參數是由 Windows 執行階段提供的字串，其中包含所需的執行時間類別名稱。

6. 建立 `IDeviceWatcher` 物件。

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. 使用 `Callback` 函數來訂閱 `Added`、`EnumerationCompleted`和 `Stopped` 事件。

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added` 事件處理常式會遞增列舉裝置的計數。 在找到十個裝置之後，它就會停止列舉進程。

   `Stopped` 事件處理常式會移除事件處理常式，並設定完成事件。

   `EnumerationCompleted` 事件處理常式會停止列舉進程。 如果有少於10部裝置，我們會處理此事件。

   > [!TIP]
   > 這個範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件（函子）、函數指標或[std：： function](../../standard-library/function-class.md)物件。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

8. 啟動列舉進程。

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. 等候列舉程式完成，然後列印訊息。 所有 `ComPtr` 和 RAII 物件都會離開範圍，並自動釋放。

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `wrl-consume-events.cpp` 的檔案中，然後在 [ **Visual Studio 命令提示**字元] 視窗中執行下列命令。

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)
