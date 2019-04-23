---
title: HOW TO：使用 WRL 處理事件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 959a85d6cf6de666ae56d09035acefe9a3828ae8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033173"
---
# <a name="how-to-handle-events-using-wrl"></a>HOW TO：使用 WRL 處理事件

本文件說明如何使用 Windows 執行階段C++範本庫 (WRL) 訂閱，以及處理 Windows 執行階段物件的事件。

如需更基本的範例，會建立該元件的執行個體，並擷取屬性值，請參閱[How to:啟動與使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。

## <a name="subscribing-to-and-handling-events"></a>訂閱和處理事件

下列步驟開始`ABI::Windows::System::Threading::IDeviceWatcher`物件，並使用事件處理常式來監視進度。 `IDeviceWatcher`介面可讓您以非同步的方式，或在背景中，列舉的裝置，並且新增、 移除或變更裝置時收到通知。 [回呼](callback-function-wrl.md)函式是此範例中很重要的一部分，因為它可讓以指定事件處理常式處理背景作業的結果。 完整的範例如下。

> [!WARNING]
> 雖然您通常會使用 Windows 執行階段C++的通用 Windows 平台應用程式，此範例中的範本程式庫會用於圖例中的主控台應用程式。 這類函式`wprintf_s`所沒有的通用 Windows 平台應用程式。 如需類型和您可以使用通用 Windows 平台應用程式中的函式的詳細資訊，請參閱[通用 Windows 平台應用程式不支援的 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)並[Win32 與 UWP 應用程式的 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

1. 包含 (`#include`) 任何所需的 Windows 執行階段，Windows 執行階段C++範本程式庫，或C++標準程式庫標頭。

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` 宣告列舉裝置所需的類型。

   建議您利用`using namespace`在.cpp 檔案中，讓程式碼更容易閱讀的指示詞。

2. 宣告應用程式的本機變數。 此範例中保留的列舉的裝置與註冊權杖，讓它在稍後取消訂閱事件數目的計數。

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. 初始化 Windows 執行階段。

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. 建立[事件](event-class-wrl.md)同步處理完成的主要應用程式的列舉型別程序的物件。

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > 這個事件是針對只為一部分的主控台應用程式的示範。 此範例會使用事件來確保應用程式結束之前會完成非同步作業。 在大部分的應用程式，您通常不等待非同步作業完成。

5. 建立啟用 factory`IDeviceWatcher`介面。

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Windows 執行階段會使用完整名稱來識別類型。 `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`參數是由 Windows 執行階段，並包含必要的執行階段類別名稱的字串。

6. 建立`IDeviceWatcher`物件。

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. 使用`Callback`函式來訂閱`Added`， `EnumerationCompleted`，和`Stopped`事件。

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added`事件處理常式列舉裝置的計數遞增。 找不到 10 的裝置之後，它就會停止列舉程序。

   `Stopped`事件處理常式移除事件處理常式，並設定完成事件。

   `EnumerationCompleted`事件處理常式會停止列舉程序。 萬一有少於 10 個裝置，我們會處理這個事件。

   > [!TIP]
   > 此範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件 (functor)，函式指標，或是[std:: function](../../standard-library/function-class.md)物件。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

8. 開始列舉程序。

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. 等候列舉程序，以完成並列印一則訊息。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

以下是完整的範例：

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`wrl-consume-events.cpp`，然後執行下列命令中**Visual Studio 命令提示字元**視窗。

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)