---
title: "如何：使用 WRL 處理事件 | Microsoft Docs"
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
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 處理事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件將示範如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)訂閱，並處理 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件的事件。  
  
 如需建立元件的執行個體並擷取屬性值的更基本的範例，請參閱 [如何：啟動與使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
## 訂閱及處理事件。  
 下列步驟會啟動 `ABI::Windows::System::Threading::IDeviceWatcher` 物件，並使用事件處理常式監控進度。  在裝置重設時，加入、移除或變更時， `IDeviceWatcher` 介面讓您能夠列舉裝置非同步，或在背景，並收到告知。  [回呼](../windows/callback-function-windows-runtime-cpp-template-library.md) 函式是此範例中很重要的一部分，因為它可以指定處理背景作業結果的事件處理常式。  完整的程式碼範例如下所示。  
  
> [!WARNING]
>  雖然您通常會在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] ，這個範例使用主控台應用程式來描述。  例如 `wprintf_s` 函式無法從 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式使用。  如需您可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用的型別和函式的詳細資訊，請參閱 [CRT 函式不支援使用 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM Windows 市集應用程式的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
1.  包含 \(`#include`\) 所有必要的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]或 Standard C\+\+ 程式庫的標頭。  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h 宣告列舉裝置所需要的型別。  
  
     建議您利用您的 .cpp 檔中的 `using namespace` 指示詞讓程式碼更容易讀取。  
  
2.  宣告應用程式的區域變數。  這個範例會持有列舉裝置和登入語彙基元數目的計數，讓它可以從事件之後取消訂閱。  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  建立同步處理列舉處理序完成繫結至主應用程式的 [事件](../windows/event-class-windows-runtime-cpp-template-library.md) 物件。  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  這個事件僅供示範使用，且僅為主控台應用程式的一部分。  這個範例會使用事件以確保在應用程式結束之前非同步作業已完成。  在多數應用程式，您通常不會等候非同步作業完成。  
  
5.  建立介面 `IDeviceWatcher` 的啟用 Factory。  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完整名稱以識別型別。  `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` 參數是由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供和包含所需的執行階段類別名稱的字串。  
  
6.  建立 `IDeviceWatcher` 物件。  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  使用 `Callback` 函式訂閱 `Added`、 `EnumerationCompleted`和 `Stopped` 事件。  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added` 事件處理常式會遞增列舉裝置的數量。  在找到十個裝置之後，即會停止列舉處理序。  
  
     `Stopped` 事件處理常式中移除事件處理常式並設定完成事件。  
  
     `EnumerationCompleted` 事件處理常式會停止列舉處理序。  為了處理小於十個的裝置的情況，我們會處理這個事件。  
  
    > [!TIP]
    >  這個範例使用 Lambda 運算式定義回呼。  您也可以使用函式物件 \(functors\)，函式指標或 [std::function](../standard-library/function-class.md) 物件。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
8.  開始列舉處理序。  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. 等候列舉型別 \(Enumeration\) 處理序完成之後列印訊息。  所有 `ComPtr` 和 RAII 物件離開範圍並自動釋放。  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 這裡有個完整範例:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## 編譯程式碼  
 若要編譯程式碼，請複製並貼到 Visual Studio 專案或貼在名為 `wrl-consume-asyncOp.cpp` 的檔案然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe wrl\-consume\-events.cpp runtimeobject.lib**  
  
## 請參閱  
 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)