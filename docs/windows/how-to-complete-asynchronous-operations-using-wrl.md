---
title: 如何： 完成非同步作業，使用 WRL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fff0a6e98dd6fdd28b1fbc2e9146d5b68975e0f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>如何：使用 WRL 完成非同步作業
本文件說明如何使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 若要啟動非同步作業和作業完成時執行工作。  
  
 這份文件會顯示兩個範例。 第一個範例會啟動非同步的計時器，並等候計時器過期。 在此範例中，您會指定非同步動作，當您建立計時器物件。 第二個範例會執行背景工作執行緒。 這個範例示範如何使用 Windows 執行階段方法會傳回`IAsyncInfo`介面。 [回呼](../windows/callback-function-windows-runtime-cpp-template-library.md)函式是這兩個範例中很重要的一部分，因為它可讓它們指定事件處理常式處理非同步作業的結果。  
  
 如需更基本的範例，以建立元件的執行個體，並擷取屬性值，請參閱[How to： 啟用和使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
> [!TIP]
>  這些範例會使用 lambda 運算式來定義回呼。 您也可以使用函式物件 (functor)，函式指標或[std:: function](../standard-library/function-class.md)物件。 如需 c + + lambda 運算式的詳細資訊，請參閱[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
## <a name="example-working-with-a-timer"></a>範例： 使用計時器  
 下列步驟開始非同步的計時器，並等候計時器過期。 完整的範例如下。  
  
> [!WARNING]
>  雖然您通常會使用 Windows 執行階段 c + + 樣板程式庫，在通用 Windows 平台 (UWP) 應用程式中，此範例會使用主控台應用程式的圖例。 函式，如`wprintf_s`所沒有的 UWP 應用程式。 如需型別和函式，您可以在 UWP 應用程式中使用的詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)和[Win32 和 COM 用於 UWP 應用程式](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。  
  
1.  包含 (`#include`) 任何必要的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h 宣告的類型，才能使用非同步的計時器。  
  
     我們建議您利用`using namespace`指示詞在.cpp 檔案中，讓程式碼更容易閱讀。  
  
2.  初始化 Windows 執行階段。  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  建立啟用處理站`ABI::Windows::System::Threading::IThreadPoolTimer`介面。  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     Windows 執行階段會使用完整限定名稱來識別類型。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`參數是由 Windows 執行階段提供，而且包含必要的執行階段類別名稱的字串。  
  
4.  建立[事件](../windows/event-class-windows-runtime-cpp-template-library.md)計時器回呼至主應用程式會同步處理的物件。  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  此事件是為了示範只做為主控台應用程式的一部分。 這個範例會使用事件，以確保應用程式結束前完成的非同步作業。 在大部分的應用程式，您通常不等候非同步作業完成。  
  
5.  建立`IThreadPoolTimer`兩秒之後過期的物件。 使用`Callback`函式來建立事件處理常式 (`ABI::Windows::System::Threading::ITimerElapsedHandler`物件)。  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  將訊息列印至主控台，並等候完成的計時器回呼。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 以下是完整的範例：  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`wrl-consume-async.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe wrl 取用 async.cpp runtimeobject.lib**  
  
## <a name="example-working-with-a-background-thread"></a>範例： 使用背景執行緒  
 下列步驟啟動背景工作執行緒，並定義該執行緒所執行的動作。 完整的範例如下。  
  
> [!TIP]
>  此範例示範如何使用`ABI::Windows::Foundation::IAsyncAction`介面。 您可以將此模式套用到實作任何介面`IAsyncInfo`: `IAsyncAction`， `IAsyncActionWithProgress`， `IAsyncOperation`，和`IAsyncOperationWithProgress`。  
  
1.  包含 (`#include`) 任何必要的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h 宣告的類型，才能使用背景工作執行緒。  
  
     我們建議您改用`using namespace`指示詞在.cpp 檔案中，讓程式碼更容易閱讀。  
  
2.  初始化 Windows 執行階段。  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  建立啟用處理站`ABI::Windows::System::Threading::IThreadPoolStatics`介面。  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  建立[事件](../windows/event-class-windows-runtime-cpp-template-library.md)同步處理至主應用程式的背景工作執行緒完成的物件。  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  此事件是為了示範只做為主控台應用程式的一部分。 這個範例會使用事件，以確保應用程式結束前完成的非同步作業。 在大部分的應用程式，您通常不等候非同步作業完成。  
  
5.  呼叫`IThreadPoolStatics::RunAsync`方法來建立背景工作執行緒。 使用`Callback`函式定義的動作。  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime`函式定義中完整的範例所示。  
  
6.  將訊息列印至主控台，並等候完成的執行緒。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 以下是完整的範例：  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`wrl-consume-asyncOp.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe wrl 取用 asyncOp.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)
