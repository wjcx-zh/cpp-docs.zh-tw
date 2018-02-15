---
title: "逐步解說： 建立使用 WRL 和媒體基礎的 UWP 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a104cab9ec15872fe9e1b1c7a1eaf7ccd705f7d2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>逐步解說： 建立使用 WRL 和媒體基礎的 UWP 應用程式
了解如何建立通用 Windows 平台 (UWP) 應用程式會使用 Windows 執行階段 c + + 樣板程式庫 (WRL) [Microsoft 媒體基礎](http://msdn.microsoft.com/library/windows/apps/ms694197)。  
  
 這個範例會建立自訂的媒體基礎轉換，可將灰階效果套用到從網路攝影機擷取的映像。 應用程式會使用 C++ 定義自訂的轉換，並使用 C# 以使用元件來轉換擷取的映像。  
  
> [!NOTE]
>  如果不使用 C#，您也可以改用 JavaScript、Visual Basic 或 C++ 使用自訂轉換元件。  
  

 在大部分情況下，您可以使用 C + + /CX 建立 Windows 執行階段)。 不過，有時候您必須使用 WRL。 比方說，當您建立 Microsoft 媒體基礎的媒體延伸時，您必須建立實作 COM 和 Windows 執行階段介面的元件。 因為 C + + /CX 只能建立 Windows 執行階段物件，若要建立媒體延伸，您必須使用 WRL 因為它可讓 COM 和 Windows 執行階段介面的實作。  

  
> [!NOTE]
>  雖然這個程式碼範例很長，它會示範建立有用的媒體基礎轉換所需的最小值。 您可以將之做為您自訂轉換的起點。 這個範例是改自[媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)、 哪些使用媒體延伸將效果套用到視訊、 解碼視訊，並建立產生媒體資料流的配置處理常式。  
  
## <a name="prerequisites"></a>必要條件  
  
-   體驗[Windows 執行階段](http://msdn.microsoft.com/library/windows/apps/br211377.aspx)。  
  
-   COM 的體驗。  
  
-   網路攝影機。  
  
## <a name="key-points"></a>重點  
  
-   若要建立自訂的媒體基礎元件，請使用 Microsoft 介面定義語言 (MIDL) 定義檔案以定義介面，實作該介面，然後使其可從其他元件啟動。  
  
-   `namespace`和`runtimeclass`屬性，而`NTDDI_WIN8`[版本](http://msdn.microsoft.com/en-us/66ac5cf3-2230-44fd-aaf6-8013e4a4ae81)屬性值會使用 WRL 的媒體基礎元件而言是 MIDL 定義的重要部分。  
  
-   [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md)是自訂媒體基礎元件的基底類別。 [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md)列舉值，提供作為範本引數，標記用於做為 Windows 執行階段類別，以及做為傳統的 COM 執行階段類別的類別。  
  
-   [InspectableClass](../windows/inspectableclass-macro.md)巨集會實作基本的 COM 功能，例如參考計數和`QueryInterface`方法，並設定執行階段類別名稱和信任層級。  
  
-   使用 microsoft:: wrl::[模組類別](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe/locales/en-US)實作 DLL 進入點函式，例如[DllGetActivationFactory](http://msdn.microsoft.com/library/br205771.aspx)， [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368\(v=vs.85\).aspx)，和[DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/ms680760\(v=vs.85\).aspx)。  
  
-   將您的元件 DLL 連結至 runtimeobject.lib。 也指定[/WINMD](../cppcx/compiler-and-linker-options-c-cx.md)產生 Windows 中繼資料的連結器列。  
  
-   讓 UWP 應用程式都能存取 WRL 元件使用專案參考。  
  
### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>若要使用 WRL 建立媒體基礎灰階轉換元件  
  
1.  在 Visual Studio 中建立**空白方案**專案。 為專案命名，例如`MediaCapture`。  
  
2.  新增**DLL (通用 Windows)**專案加入方案。 為專案命名，例如`GrayscaleTransform`。  
  
3.  新增**Midl 檔 (.idl)**檔案加入專案中。 為檔案命名，例如`GrayscaleTransform.idl`。  
  
4.  將此程式碼新增至 GrayscaleTransform.idl。  
  
     [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]  
  
5.  使用下列程式碼取代 pch.h 的內容。  
  
     [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]  
  
6.  將新的標頭檔加入專案中，它`BufferLock.h`，然後新增此程式碼：  
  
     [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]  
  
7.  不會在此範例中使用 GrayscaleTransform.h。 您可以選擇將之從專案移除。  
  
8.  使用下列程式碼取代 GrayscaleTransform.cpp 的內容。  
  
     [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]  
  
9. 將新的模組定義檔加入專案中，它`GrayscaleTransform.def`，然後新增此程式碼：  
  
   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```   
  
10. 使用下列程式碼取代 dllmain.cpp 的內容。  
  
     [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]  
  
11. 在專案的**屬性頁**對話方塊方塊中，設定下列**連結器**屬性。  
  
    1.  在下**輸入**，如**模組定義檔**，指定`GrayScaleTransform.def`。  
  
    2.  也在**輸入**，新增`runtimeobject.lib`， `mfuuid.lib`，和`mfplatf.lib`至**其他相依性**屬性。  
  
    3.  在下**Windows 中繼資料**，將**產生 Windows 中繼資料**至**是 (/ WINMD)**。  
  
### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>若要使用 WRL 的自訂媒體基礎元件從 C# 應用程式  
  
1.  加入新**C# 空白應用程式 (XAML)**專案加入`MediaCapture`方案。 為專案命名，例如`MediaCapture`。  
  
2.  在**MediaCapture**專案中，將參考加入`GrayscaleTransform`專案。 若要了解作法，請參閱[如何： 加入或移除參考使用參考管理員](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。  
  
3.  在 Package.appxmanifest 中上**功能**索引標籤上，選取**麥克風**和**網路攝影機**。 這兩種功能是從網路攝影機擷取相片的必要項。  
  
4.  在 MainPage.xaml 中，將此程式碼加入至根[方格](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)項目：  
  
     [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]  
  
5.  使用下列程式碼取代 MainPage.xaml.cs 的內容。  
  
     [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]  
  
 下圖顯示 MediaCapture 應用程式。  
  
 ![擷取相片的 MediaCapture 應用程式](../windows/media/wrl_media_capture.png "WRL_Media_Capture")  
  
## <a name="next-steps"></a>後續步驟  
 此範例示範如何一次從預設網路攝影機擷取相片。 [媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)更多。 它會示範如何列舉網路攝影機裝置，並使用本機配置處理常式，以及示範在個別相片和視訊資料流上運作的其他媒體效果。  
  
## <a name="see-also"></a>請參閱  
 [Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft 媒體基礎](http://msdn.microsoft.com/library/windows/apps/ms694197)   
 [媒體延伸範例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)