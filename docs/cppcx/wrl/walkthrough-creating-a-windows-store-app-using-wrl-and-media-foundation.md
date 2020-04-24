---
title: 逐步解說： 使用 WRL 與媒體基礎建立 UWP 應用程式
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031507"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>逐步解說： 使用 WRL 與媒體基礎建立 UWP 應用程式

> [!NOTE]
> 對於新的 UWP 應用和元件,我們建議您使用[C++/WinRT,](/windows/uwp/cpp-and-winrt-apis/)這是 Windows 運行時 API 的新標準 C++17 語言投影。 從版本 1803 起,C++/WinRT 在 Windows 10 SDK 中可用。 C++/WinRT 完全在標頭檔中實現,旨在為您提供對現代 Windows API 的一流訪問許可權。

在本教學中,您將學習如何使用 Windows 執行時 C++樣本庫 (WRL) 創建使用[Microsoft 媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk)的通用 Windows 平臺 (UWP) 應用。

這個範例會建立自訂的媒體基礎轉換，可將灰階效果套用到從網路攝影機擷取的映像。 應用程式會使用 C++ 定義自訂的轉換，並使用 C# 以使用元件來轉換擷取的映像。

> [!NOTE]
> 如果不使用 C#，您也可以改用 JavaScript、Visual Basic 或 C++ 使用自訂轉換元件。

在大多數情況下,可以使用C++/CX創建Windows運行時。 但是,有時您必須使用 WRL。 例如,在為 Microsoft 媒體基礎創建媒體擴展時,必須創建實現 COM 和 Windows 執行時介面的元件。 由於C++/CX 只能創建 Windows 運行時物件,因此必須使用 WRL,因為它支援實現 COM 和 Windows 執行時介面。

> [!NOTE]
> 雖然這個程式碼範例很長，它會示範建立有用的媒體基礎轉換所需的最小值。 您可以將之做為您自訂轉換的起點。 此示例根據[Media 擴展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)改編,該示例使用媒體擴展將效果應用於視頻、解碼視頻以及創建生成媒體流的方案處理程式。

## <a name="prerequisites"></a>先決條件

- 在 Visual Studio 2017 及更高版本中,UWP 支援是可選元件。 要安裝它,請從 Windows "開始"功能表打開視覺化工作室安裝程式,然後查找您的視覺工作室版本。 選擇 **"修改**",然後確保選中**通用 Windows 平台開發**磁貼。 在 **「可選元件**」下,檢查 Visual Studio 2017 的**UWP C++工具 (v141),** 檢查 Visual Studio 2019**的 C++工具(v142)。** 然後檢查要使用的 Windows SDK 版本。

- 體驗[Windows 執行時](/uwp/api/)。

- COM 的體驗。

- 網路攝影機。

## <a name="key-points"></a>重點

- 若要建立自訂的媒體基礎元件，請使用 Microsoft 介面定義語言 (MIDL) 定義檔案以定義介面，實作該介面，然後使其可從其他元件啟動。

- 和`namespace``runtimeclass`屬性以及`NTDDI_WIN8`[版本](/windows/win32/Midl/version)屬性值是使用 WRL 的媒體基礎元件的 MIDL 定義的重要組成部分。

- [Microsoft:WRL:運行時類](runtimeclass-class.md)是自定義媒體基礎元件的基礎類。 [Microsoft::WRL::運行時類類型::WinRtClassicComMix](runtimeclasstype-enumeration.md)枚舉值(作為範本參數提供)將類標記為 Windows 運行時類和經典 COM 運行時類。

- ["可檢查類"](inspectableclass-macro.md)宏實現基本的 COM 功能`QueryInterface`,如引用 計數和方法,並設置運行時類名稱和信任級別。

- 使用 Microsoft::WRL::[模組類](module-class.md)實現 DLL 入口點函數,如[DllGet 啟動工廠](/windows/win32/winrt/functions)[、DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和[DllGetClassObject。](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)

- 將您的元件 DLL 連結至 runtimeobject.lib。 還在連結器行上指定[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md)以生成 Windows 元數據。

- 使用專案引用使 WWP 應用可以造訪 WRL 元件。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>使用 WRL 建立媒體基礎灰度變換元件

1. 在可視化工作室中,創建**一個空白解決方案**專案。 命名項目,例如,*媒體擷取*。

1. 向解決方案添加**DLL(通用 Windows)** 專案。 命名項目,例如,*灰階變換*。

1. 將**Midl 檔案 (.idl)** 檔案新增到專案中。 命名檔案,例如,*灰階轉換.idl*。

1. 將此代碼加入到灰階轉換.idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 使用以下代碼取代的內容`pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 新增新標頭檔,命名它`BufferLock.h`,然後將內容取代此代碼:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`此示例中不使用。 您可以選擇將之從專案移除。

1. 使用以下代碼取代的內容`GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 新增模組定義檔案,命名它`GrayscaleTransform.def`,然後新增此代碼:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 使用以下代碼取代的內容`dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. 在項目**的屬性頁**對話方塊中,設置以下**連結器**屬性。

   1. 在 **「輸入**」下,對於**模組定義檔案**`GrayScaleTransform.def`,指定 。

   1. 還在 **「輸入**」`runtimeobject.lib`下`mfuuid.lib`,添加`mfplat.lib`和添加到 **「附加依賴項」** 屬性。

   1. 在**Windows 中數據**下,將 **「生成 Windows 母資料」** 設定為 **「是」(/WINMD)。**

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>使用來自 C# 應用中的自訂媒體基礎元件

1. 向`MediaCapture`解決方案添加新的**C# 空白應用(通用 Windows)** 專案。 命名項目,例如,*媒體擷取*。

1. 在**MediaCapture**專案中,添加對`GrayscaleTransform`專案的引用。 要瞭解如何[使用:使用參考管理員加入或刪除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。

1. 在`Package.appxmanifest`「**功能」** 選項卡上,選擇 **「麥克風**」和 **「網路攝像頭**」。 這兩種功能是從網路攝影機擷取相片的必要項。

1. 在`MainPage.xaml`中,將此代碼加入到根[網格](/uwp/api/windows.ui.xaml.controls.grid)元素:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 使用以下代碼取代的內容`MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

下圖顯示了`MediaCapture app`。

![擷取相片的 MediaCapture 應用程式](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>後續步驟

此範例示範如何一次從預設網路攝影機擷取相片。 [媒體擴展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)執行更多工作。 它會示範如何列舉網路攝影機裝置，並使用本機配置處理常式，以及示範在個別相片和視訊資料流上運作的其他媒體效果。

## <a name="see-also"></a>另請參閱

[Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[微軟媒體基金會](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[媒體擴展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
