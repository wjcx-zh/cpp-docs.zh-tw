---
title: 逐步解說：建立 UWP 應用程式使用 WRL 和媒體基礎
ms.date: 09/17/2018
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: e0254be8c6fa185f75c46898d4da51742195550a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036032"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>逐步解說：建立 UWP 應用程式使用 WRL 和媒體基礎

了解如何建立通用 Windows 平台 (UWP) 應用程式會使用 Windows 執行階段 c + + 範本庫 (WRL) [Microsoft 媒體基礎](/windows/desktop/medfound/microsoft-media-foundation-sdk)。

這個範例會建立自訂的媒體基礎轉換，可將灰階效果套用到從網路攝影機擷取的映像。 應用程式會使用 C++ 定義自訂的轉換，並使用 C# 以使用元件來轉換擷取的映像。

> [!NOTE]
> 如果不使用 C#，您也可以改用 JavaScript、Visual Basic 或 C++ 使用自訂轉換元件。

在大部分情況下，您可以使用 C + + /CX，以建立 Windows 執行階段。 不過，有時候您必須使用 WRL。 例如，當您建立 Microsoft 媒體基礎的媒體延伸模組，您必須建立實作 COM 和 Windows 執行階段介面的元件。 因為 C + + /CX 只能建立 Windows 執行階段物件，以建立媒體延伸，您必須使用 WRL 因為它可讓 COM 和 Windows 執行階段介面的實作。

> [!NOTE]
> 雖然這個程式碼範例很長，它會示範建立有用的媒體基礎轉換所需的最小值。 您可以將之做為您自訂轉換的起點。 這個範例是來自[媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)、 哪些使用媒體延伸將效果套用到視訊、 解碼視訊，以及建立產生媒體資料流的配置處理常式。

## <a name="prerequisites"></a>必要條件

- 體驗[Windows 執行階段](https://msdn.microsoft.com/library/windows/apps/br211377.aspx)。

- COM 的體驗。

- 網路攝影機。

## <a name="key-points"></a>重點

- 若要建立自訂的媒體基礎元件，請使用 Microsoft 介面定義語言 (MIDL) 定義檔案以定義介面，實作該介面，然後使其可從其他元件啟動。

- `namespace`並`runtimeclass`屬性，而`NTDDI_WIN8`[版本](/windows/desktop/Midl/version)屬性值會使用 WRL 的媒體基礎元件而言是 MIDL 定義的重要部分。

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md)是自訂媒體基礎元件的基底類別。 [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](runtimeclasstype-enumeration.md)列舉值，也就提供作為範本引數，將標記用於為 Windows 執行階段類別和傳統的 COM 執行階段類別的類別。

- [InspectableClass](inspectableclass-macro.md)巨集會實作基本的 COM 功能，例如參考計數和`QueryInterface`方法，並設定執行階段類別名稱和信任層級。

- 使用 microsoft:: wrl::[模組類別](module-class.md)實作的 DLL 進入點函式，例如[DllGetActivationFactory](https://msdn.microsoft.com/library/br205771.aspx)， [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)，和[DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject)。

- 將您的元件 DLL 連結至 runtimeobject.lib。 也指定[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md)連結器列來產生 Windows 中繼資料。

- 使用 UWP 應用程式供 WRL 元件的專案參考。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>若要使用 WRL 建立媒體基礎灰階轉換元件

1. 在 Visual Studio 中建立**空白方案**專案。 為專案命名，例如*MediaCapture*。

1. 新增**DLL (通用 Windows)** 專案加入方案。 為專案命名，例如*GrayscaleTransform*。

1. 新增**Midl 檔 (.idl)** 檔案加入專案。 將檔案命名為，比方說， *GrayscaleTransform.idl*。

1. 將此程式碼新增至 GrayscaleTransform.idl 中：

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 使用下列程式碼的內容取代`pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 將新的標頭檔新增至專案，將其命名`BufferLock.h`，然後將內容取代此程式碼：

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` 不會用於此範例中。 您可以選擇將之從專案移除。

1. 使用下列程式碼的內容取代`GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 將新的模組定義檔加入至專案，將其命名`GrayscaleTransform.def`，然後新增此程式碼：

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 使用下列程式碼的內容取代`dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. 在專案的**屬性頁**對話方塊方塊中，設定下列**連結器**屬性。

   1. 底下**輸入**，如**模組定義檔**，指定`GrayScaleTransform.def`。

   1. 之下，而且**輸入**，新增`runtimeobject.lib`， `mfuuid.lib`，並`mfplat.lib`來**其他相依性**屬性。

   1. 底下**Windows 中繼資料**，將**產生 Windows 中繼資料**來**是 (/ WINMD)**。

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>若要使用 WRL 自訂媒體基礎元件從 C# 應用程式

1. 加入新**C# 空白應用程式 (通用 Windows)** 專案加入`MediaCapture`解決方案。 為專案命名，例如*MediaCapture*。

1. 在  **MediaCapture**專案中，將參考加入`GrayscaleTransform`專案。 若要深入了解，請參閱[How to:使用參考管理員新增或移除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。

1. 在  `Package.appxmanifest`，請在**功能**索引標籤上，選取**麥克風**並**網路攝影機**。 這兩種功能是從網路攝影機擷取相片的必要項。

1. 在  `MainPage.xaml`，將此程式碼新增至根[格線](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)項目：

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 使用下列程式碼的內容取代`MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

下圖顯示`MediaCapture app`。

![擷取相片的 MediaCapture 應用程式](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>後續步驟

此範例示範如何一次從預設網路攝影機擷取相片。 [媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)執行其他作業。 它會示範如何列舉網路攝影機裝置，並使用本機配置處理常式，以及示範在個別相片和視訊資料流上運作的其他媒體效果。

## <a name="see-also"></a>另請參閱

[Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft 媒體基礎](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)