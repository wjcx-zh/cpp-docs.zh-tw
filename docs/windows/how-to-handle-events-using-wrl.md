---
title: 如何： 使用 WRL 處理事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3c1666d1c79414beddc5b5e3ccc03953c92e902
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-handle-events-using-wrl"></a>如何：使用 WRL 處理事件
本文件說明如何使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 訂閱和處理 Windows 執行階段物件的事件。  
  
 如需更基本的範例，以建立該元件的執行個體，並擷取屬性值，請參閱[How to： 啟用和使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
## <a name="subscribing-to-and-handling-events"></a>訂閱和處理事件  
 下列步驟開始`ABI::Windows::System::Threading::IDeviceWatcher`物件，並使用事件處理常式來監視進度。 `IDeviceWatcher`介面可讓您以非同步的方式，或在背景中列舉的裝置和裝置新增、 移除或變更時收到通知。 [回呼](../windows/callback-function-windows-runtime-cpp-template-library.md)函式是此範例中的重要部分，因為它可讓它指定處理結果的背景作業的事件處理常式。 完整的範例如下。  
  
> [!WARNING]
>  雖然您通常會使用 Windows 執行階段 c + + 樣板程式庫，在通用 Windows 平台應用程式中，此範例會使用主控台應用程式的圖例。 函式，如`wprintf_s`所沒有的通用 Windows 平台應用程式。 多個型別和函式，您可以使用通用 Windows 平台應用程式中的詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)和[Win32 和 COM 用於 UWP 應用程式](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。  
  
1.  包含 (`#include`) 任何必要的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h 宣告列舉裝置所需的類型。  
  
     我們建議您利用`using namespace`指示詞在.cpp 檔案中，讓程式碼更容易閱讀。  
  
2.  宣告的應用程式的本機變數。 這個範例會保存列舉的裝置註冊權杖，使其在稍後取消訂閱事件數目的計數。  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  初始化 Windows 執行階段。  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  建立[事件](../windows/event-class-windows-runtime-cpp-template-library.md)同步處理完成的主要應用程式的列舉型別程序的物件。  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  此事件是為了示範只做為主控台應用程式的一部分。 這個範例會使用事件，以確保應用程式結束前完成的非同步作業。 在大部分的應用程式，您通常不等候非同步作業完成。  
  
5.  建立啟用處理站`IDeviceWatcher`介面。  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     Windows 執行階段會使用完整限定名稱來識別類型。 `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`參數是由 Windows 執行階段提供，而且包含必要的執行階段類別名稱的字串。  
  
6.  建立`IDeviceWatcher`物件。  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  使用`Callback`函式來訂閱`Added`， `EnumerationCompleted`，和`Stopped`事件。  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added`事件處理常式列舉裝置的計數遞增。 找不到 10 的裝置之後，它就會停止列舉程序。  
  
     `Stopped`事件處理常式中移除事件處理常式，並設定完成事件。  
  
     `EnumerationCompleted`事件處理常式會停止列舉程序。 萬一發生少於 10 個裝置，我們會處理這個事件。  
  
    > [!TIP]
    >  這個範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件 (functor)，函式指標或[std:: function](../standard-library/function-class.md)物件。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
8.  開始列舉處理序。  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. 等候列舉處理序完成，然後列印訊息。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 以下是完整的範例：  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`wrl-consume-events.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe wrl 取用 events.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)