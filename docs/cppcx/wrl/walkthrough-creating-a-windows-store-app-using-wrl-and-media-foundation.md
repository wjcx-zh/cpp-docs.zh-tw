---
title: 逐步解說：使用 WRL 和媒體基礎建立 UWP 應用程式
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: fecfc83e674c418a920e3dd73149f4d6294090fa
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404921"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>逐步解說：使用 WRL 和媒體基礎建立 UWP 應用程式

> [!NOTE]
> 針對新的 UWP 應用程式和元件，建議您使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)，這是適用于 Windows 執行階段 api 的新 Standard c + + 17 語言投影。 從1803版開始，Windows 10 SDK 中提供 c + +/WinRT。 C + +/WinRT 完全實作為標頭檔，其設計目的是為您提供現代化 Windows API 的第一級存取。

在本教學課程中，您將瞭解如何使用 Windows 執行階段 c + + Template Library （WRL）來建立使用[Microsoft 媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk)的通用 WINDOWS 平臺（UWP）應用程式。

這個範例會建立自訂的媒體基礎轉換，可將灰階效果套用到從網路攝影機擷取的映像。 應用程式會使用 C++ 定義自訂的轉換，並使用 C# 以使用元件來轉換擷取的映像。

> [!NOTE]
> 如果不使用 C#，您也可以改用 JavaScript、Visual Basic 或 C++ 使用自訂轉換元件。

在大部分的情況下，您可以使用 c + +/CX 來建立 Windows 執行階段。 不過，有時候您必須使用 WRL。 例如，當您建立 Microsoft 媒體基礎的媒體擴充功能時，您必須建立同時執行 COM 和 Windows 執行階段介面的元件。 因為 c + +/CX 只能建立 Windows 執行階段物件，所以若要建立媒體延伸，您必須使用 WRL，因為它可讓您同時執行 COM 和 Windows 執行階段介面。

> [!NOTE]
> 雖然這個程式碼範例很長，它會示範建立有用的媒體基礎轉換所需的最小值。 您可以將之做為您自訂轉換的起點。 這個範例是從[媒體延伸模組範例](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)進行調整，其使用媒體延伸模組將效果套用至影片、解碼影片，以及建立會產生媒體資料流程的配置處理常式。

## <a name="prerequisites"></a>必要條件

- 在 Visual Studio 2017 和更新版本中，UWP 支援是選擇性元件。 若要安裝它，請從 Windows [開始] 功能表開啟 [Visual Studio 安裝程式，然後尋找您的 Visual Studio 版本。 選擇 [**修改**]，然後確定已核取 [**通用 Windows 平臺開發**] 磚。 在 [**選用元件**] 下，檢查適用于 Visual Studio 2017 的 [適用于**uwp 的 c + + 工具（v141）** ] 或 [適用于 Visual Studio 2019 的**c + + 工具** 然後檢查您要使用的 Windows SDK 版本。

- 體驗[Windows 執行階段](/uwp/api/)。

- COM 的體驗。

- 網路攝影機。

## <a name="key-points"></a>重點

- 若要建立自訂的媒體基礎元件，請使用 Microsoft 介面定義語言 (MIDL) 定義檔案以定義介面，實作該介面，然後使其可從其他元件啟動。

- `namespace`和 `runtimeclass` 屬性，而 `NTDDI_WIN8` [version](/windows/win32/Midl/version)屬性值則是使用 WRL 之媒體基礎元件的 MIDL 定義的重要部分。

- [Microsoft：： WRL：： RuntimeClass](runtimeclass-class.md)是自訂媒體基礎元件的基類。 提供做為樣板引數的[Microsoft：： WRL：： RuntimeClassType：： WinRtClassicComMix](runtimeclasstype-enumeration.md)列舉值會標記類別，以當做 Windows 執行階段類別和傳統 COM 執行時間類別使用。

- [InspectableClass](inspectableclass-macro.md)宏會執行基本的 COM 功能，例如參考計數和 `QueryInterface` 方法，並設定執行時間類別名稱和信任層級。

- 使用 Microsoft：： WRL：：[Module 類別](module-class.md)來執行 DLL 進入點函式，例如[DllGetActivationFactory](/windows/win32/winrt/functions)、 [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和[DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)。

- 將您的元件 DLL 連結至 runtimeobject.lib。 此外，也請在連結器行上指定[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) ，以產生 Windows 中繼資料。

- 使用專案參考，讓 UWP 應用程式可以存取 WRL 元件。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>若要使用 WRL 建立媒體基礎灰階轉換元件

1. 在 Visual Studio 中，建立**空白方案**專案。 為專案命名，例如*MediaCapture*。

1. 將 [ **DLL （通用 Windows）** ] 專案新增至方案。 為專案命名，例如*GrayscaleTransform*。

1. 將**Midl 檔案（.idl）** 檔案加入至專案。 將檔案命名為，例如*GrayscaleTransform。*

1. 將此程式碼新增至 GrayscaleTransform：

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 使用下列程式碼取代的內容 `pch.h` ：

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 將新的標頭檔新增至專案，並將其命名為 `BufferLock.h` ，然後以下列程式碼取代內容：

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`在此範例中不會使用。 您可以選擇將之從專案移除。

1. 使用下列程式碼取代的內容 `GrayscaleTransform.cpp` ：

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 將新的模組定義檔案加入至專案，並將其命名為 `GrayscaleTransform.def` ，然後新增下列程式碼：

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 使用下列程式碼取代的內容 `dllmain.cpp` ：

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. 在專案的 [**屬性頁**] 對話方塊中，設定下列**連結器**屬性。

   1. 在 [**輸入**] 下，針對**模組定義**檔案指定 `GrayScaleTransform.def` 。

   1. 此外，在 [**輸入**] 底下，將 `runtimeobject.lib` 、 `mfuuid.lib` 和新增 `mfplat.lib` 至 [其他相依性 **]** 屬性。

   1. 在 [ **Windows 中繼資料**] 下，將 [**產生 Windows 中繼資料**] 設定為 **[是（/WINMD）**

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>若要從 c # 應用程式使用 WRL 自訂媒體基礎元件

1. 將新的**c # [空白應用程式（通用 Windows）** ] 專案加入至 `MediaCapture` 方案。 為專案命名，例如*MediaCapture*。

1. 在**MediaCapture**專案中，加入專案的參考 `GrayscaleTransform` 。 若要瞭解方法，請參閱[如何：使用參考管理員加入或移除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。

1. 在 `Package.appxmanifest` 的 [**功能**] 索引標籤上，選取 [**麥克風**和**網路**攝影機]。 這兩種功能是從網路攝影機擷取相片的必要項。

1. 在中 `MainPage.xaml` ，將下列程式碼新增至根[方格](/uwp/api/windows.ui.xaml.controls.grid)元素：

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 使用下列程式碼取代的內容 `MainPage.xaml.cs` ：

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

下圖顯示 `MediaCapture app` 。

![擷取相片的 MediaCapture 應用程式](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>後續步驟

此範例示範如何一次從預設網路攝影機擷取相片。 [媒體延伸模組範例](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)會執行更多工作。 它會示範如何列舉網路攝影機裝置，並使用本機配置處理常式，以及示範在個別相片和視訊資料流上運作的其他媒體效果。

## <a name="see-also"></a>另請參閱

[Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft 媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk)
