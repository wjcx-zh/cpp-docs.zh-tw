---
title: "如何：使用 WRL 完成非同步作業 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 完成非同步作業
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件將示範如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 啟動非同步作業和執行工作，當作業完成時。  
  
 這個文件顯示兩個範例。  第一個範例會啟動非同步計時器並等候計時器逾時。  在此範例中，在您建立計時器物件時，您會指定非同步動作。  第二個範例會執行背景工作執行緒。  這個範例示範如何使用傳回 `IAsyncInfo` 介面的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 方法一起使用。  因為它可讓它們指定事件處理常式處理非同步作業的結果， [回呼](../windows/callback-function-windows-runtime-cpp-template-library.md) 函式是兩個範例中重要的一部分。  
  
 如需建立元件的執行個體並擷取屬性值的更基本的範例，請參閱 [如何：啟動與使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
> [!TIP]
>  這些範例會使用 Lambda 運算式定義回呼。  您也可以使用函式物件 \(functors\)，函式指標或 [std::function](../standard-library/function-class.md) 物件。  如需 C\+\+ Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
## 範例:使用計時器。  
 下列步驟會啟動非同步計時器並等候計時器逾時。  完整的程式碼範例如下所示。  
  
> [!WARNING]
>  雖然您通常會在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] ，這個範例使用主控台應用程式來描述。  例如 `wprintf_s` 函式無法從 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式使用。  如需您可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用的型別和函式的詳細資訊，請參閱 [\/ZW 不支援使用 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM Windows 市集應用程式的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
1.  包含 \(`#include`\) 所有必要的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]或 Standard C\+\+ 程式庫的標頭。  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h 宣告時必須使用非同步計時器的型別。  
  
     建議您利用您的 .cpp 檔中的 `using namespace` 指示詞讓程式碼更容易讀取。  
  
2.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  建立介面 `ABI::Windows::System::Threading::IThreadPoolTimer` 的啟用 Factory。  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完整名稱以識別型別。  `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` 參數是由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供和包含所需的執行階段類別名稱的字串。  
  
4.  建立同步處理計時器回呼至主應用程式的 [事件](../windows/event-class-windows-runtime-cpp-template-library.md) 物件。  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  這個事件僅供示範使用，且僅為主控台應用程式的一部分。  這個範例會使用事件以確保在應用程式結束之前非同步作業已完成。  在多數應用程式，您通常不會等候非同步作業完成。  
  
5.  建立會在兩秒後過期的 `IThreadPoolTimer` 物件。  使用 `Callback` 函式建立事件處理常式\( `ABI::Windows::System::Threading::ITimerElapsedHandler` 物件\)。  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  將訊息列印至主控台並等候計時器回呼完成。  所有 `ComPtr` 和 RAII 物件離開範圍並自動釋放。  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 這裡有個完整範例:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### 編譯程式碼  
 若要編譯程式碼，請複製並貼到 Visual Studio 專案或貼在名為 `wrl-consume-async.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令的檔案。  
  
 **cl.exe wrl\-consume\-async.cpp runtimeobject.lib**  
  
## 範例:使用背景執行緒。  
 下列步驟會啟動背景工作執行緒並定義由該執行緒執行的動作。  完整的程式碼範例如下所示。  
  
> [!TIP]
>  這個範例示範如何使用 `ABI::Windows::Foundation::IAsyncAction` 介面。  您可以將該樣式套用至任何實作介面的 `IAsyncInfo`: `IAsyncAction`、 `IAsyncActionWithProgress`、 `IAsyncOperation`和 `IAsyncOperationWithProgress`。  
  
1.  包含 \(`#include`\) 所有必要的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]或 Standard C\+\+ 程式庫的標頭。  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h 宣告時必須使用背景工作執行緒的型別。  
  
     建議您利用您的 .cpp 檔中的 `using namespace` 指示詞讓程式碼更容易讀取。  
  
2.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  建立介面 `ABI::Windows::System::Threading::IThreadPoolStatics` 的啟用 Factory。  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  建立同步處理背景工作執行緒完成繫結至主應用程式的 [事件](../windows/event-class-windows-runtime-cpp-template-library.md) 物件。  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  這個事件僅供示範使用，且僅為主控台應用程式的一部分。  這個範例會使用事件以確保在應用程式結束之前非同步作業已完成。  在多數應用程式，您通常不會等候非同步作業完成。  
  
5.  呼叫方法 `IThreadPoolStatics::RunAsync` 建立背景工作執行緒。  使用 `Callback` 函式定義這個動作。  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime` 函式在後面的完整範例中所定義。  
  
6.  將訊息列印至主控台並等候執行緒完成。  所有 `ComPtr` 和 RAII 物件離開範圍並自動釋放。  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 這裡有個完整範例:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### 編譯程式碼  
 若要編譯程式碼，請複製並貼到 Visual Studio 專案或貼在名為 `wrl-consume-asyncOp.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令的檔案。  
  
 **cl.exe wrl\-consume\-asyncOp.cpp runtimeobject.lib**  
  
## 請參閱  
 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)