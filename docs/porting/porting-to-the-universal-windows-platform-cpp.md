---
title: 移植到通用 Windows 平台 (C++)
ms.date: 10/23/2019
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: 0013d85ad8c27c06560c9f9e541691f4335252d1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076842"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>移植到通用 Windows 平台 (C++)

在本主題中，您可以找到有關如何移植現有 C++ 程式碼到 Windows 10 應用程式平台 (通用 Windows 平台) 的詳細資訊。 「*通用*」一詞的意思是，您的程式碼可以在任何執行 Windows 10 的裝置上執行。 您可以建立在執行 Windows 10 之任何裝置上順利運作的單一專案和單一 XAML 使用者介面。 您可以在 XAML 中使用動態配置功能，以允許應用程式的 UI 適應不同的顯示器大小。

Windows 開發人員中心文件包含如何將 Windows 8.1 應用程式移植到通用 Windows 平台的指南。 請參閱 [從 Windows 執行階段 8 移至 UWP](/windows/uwp/porting/w8x-to-uwp-root)。 雖然本指南大部分著重於 C# 程式碼，但大部分的指引也適用於 C++。 下列程序包含更詳細的資訊。 另請參閱[從桌面應用程式移至 UWP](/windows/uwp/porting/desktop-to-uwp-migrate)。

本主題包含將程式碼移植到 UWP 的程序，如下所示。

- [將 Windows 8.1 市集應用程式移植到 UWP](#BK_81StoreApp)

- [將 Windows 8.1 執行階段元件移植到 UWP](#BK_81Component)

若您有傳統桌面的 Win32 DLL，並想要從 UWP 應用程式加以呼叫，您也可以執行此作業。 使用這類程序可以為現有的傳統 Windows 桌面的 C++ 應用程式或跨平台標準 C++ 程式碼建立 UWP 使用者介面層。 請參閱[做法：在通用 Windows 平台應用程式中使用現有的 C++ 程式碼](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)。

## <a name="porting-a-windows-81-store-app-to-the-uwp"></a><a name="BK_81StoreApp"></a> 將 Windows 8.1 市集應用程式移植到 UWP

如果您有 Windows 8.1 市集應用程式，您可以使用此程序，讓它在 UWP 和執行 Windows 10 的任何裝置上運作。  最好先以 Windows 8.1 專案的 Visual Studio 2019 來建立專案，以便先排除編譯器和程式庫中的變更所引發的任何問題。 完成此作業之後，有兩種方式可將其轉換為 Windows 10 UWP 專案。 最簡單的方式 (如下列程序所述) 就是建立通用 Windows 專案，然後將現有的程式碼複製到其中。 若您是使用 Windows 8.1 桌面及 Windows 8.1 Phone 的通用專案，則您的專案將會從兩個不同的配置的 XAML 開始，但最後則會演變成可以調整成顯示器大小的單一動態配置。

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>將 Windows 8.1 市集應用程式移植到 UWP

1. 若還未如此做，請在 Visual Studio 2017 中開啟 Windows 8.1 應用程式專案，並依照指示升級專案檔。

   您必須已在 **Visual Studio 安裝程式中安裝 Windows 8.1 工具**。 若還未安裝這些工具，請從 [程式和功能] 視窗中啟動 **Visual Studio** 安裝程式，選擇 [Visual Studio 2017]，然後在安裝程式視窗中選擇 [修改]。 找出 [Windows 8.1 工具]，確認已加以選取，然後選擇 [確定]。

1. 開啟 [專案屬性] 視窗，然後在 [C++] > [一般] 中，將 [平台工具組] 設定為 **v141**，即 Visual Studio 2017 的工具組。

1. 將專案建置為 Windows 8.1 專案，並解決任何建置錯誤。 在這個階段的任何錯誤都有可能是出於建置工具和程式庫的重大變更。 如需可能會影響程式碼之變更的詳細說明，請參閱 [Visual C++ 變更歷程記錄 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)。

   一旦可以正常建置您的專案，您就已經準備好移植到通用 Windows (Windows 10) 了。

1. 使用空白範本建立新的通用 Windows 應用程式專案。 您也許想提供給它與現有專案相同的名稱，但若要這麼做，則此專案必須是在不同的目錄中。

1. 請關閉解決方案，然後使用 **Windows 檔案總管**或命令列，將程式碼檔案 (副檔名為 .cpp、.h 和 .xaml) 從 Windows 8.1 專案複製到與您在步驟 1 中所建立專案之專案檔 (.vcxproj) 相同的資料夾內。 請勿複製 Package.appxmanifest 檔案，而如果您有針對 Windows 8.1 桌面版和 Phone 的不同程式碼，請選擇其中一個先進行移植 (您稍後必須先執行一些工作，以套用到其他工作)。 請務必複製子資料夾和其內容。 如果出現提示，請選擇取代任何重複名稱的檔案。

1. 重新開啟解決方案，然後選擇專案節點捷徑功能表中的 [新增] > [現有項目]。 請選取您已複製的所有檔案，但是已為專案之一部分的任何檔案除外。

   請檢查任何子資料夾，並請確認在其中新增這些檔案。

1. 如果您不使用和舊專案相同的專案名稱，則請開啟 Package.appxmanifest 檔案，更新 [進入點] 以反映 `App` 類別的命名空間名稱。

   Package.appxmanifest 檔案中的 [進入點] 欄位包含 `App` 類別的範圍名稱，其中包括包含 `App` 類別的命名空間。 當您建立通用 Windows 專案時，此命名空間會設為專案的名稱。 如果這和從舊的專案中複製的檔案不同，則您必須更新其中之一或其他檔案，使兩者相符。

1. 建置專案，並解決任何出於 Windows SDK 不同版本之間之重大變更的建置錯誤。

1. 在本機桌面上執行專案。 請確認沒有部署錯誤，也請確認應用程式的版面配置看起來是否合理，以及是否可在桌面上正確運作。

1. 如果您有針對另一個裝置的不同程式碼檔案和 .xaml，例如 Windows Phone 8.1，請檢查這段程式碼，並識別其中何處不同於標準裝置。 如果不同之處只在於版面配置，您也許可在 xaml 中使用 **Visual State Manager**，依螢幕大小自訂顯示。 至於其他差異，您可以在使用下列 #if 陳述式的程式碼中使用條件區段。

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   這些陳述式分別適用於 UWP 應用程式、Windows Phone Store 應用程式、兩者都適用或兩者均不適用 (僅傳統 Win32 桌面)。 這些巨集只能在 Windows SDK 8.1 和更新版本中使用，因此如果您的程式碼需要使用舊版 Windows SDK 編譯或用於 Windows 以外的其他平台，那麼您也應該考慮無一定義的情況。

1. 針對應用程式支援的每個裝置類型，請在模擬器或實體裝置上執行和偵錯應用程式。 若要執行模擬器，您需要在實體電腦上執行 Visual Studio，而不是虛擬機器。

## <a name="porting-a-windows-81-runtime-component-to-the-uwp"></a><a name="BK_81Component"></a> 將 Windows 8.1 執行階段元件移植到 UWP

如果您的 DLL 或 Windows 執行階段元件已經適用於 Windows 8.1 市集應用程式，您即可使用此程序，取得適用 UWP 和 Windows 10 的元件或 DLL。 基本程序為建立新的專案，並將您的程式碼複製到其中。

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>將 Windows 8.1 執行階段元件移植到 UWP

1. 在 Visual Studio 2017 的 [新專案] 對話方塊中，找出 [Windows 通用] 節點。 如果沒有看到這個節點，請先安裝 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。 選擇 [Windows 執行階段元件] 範本，再為元件命名，然後選擇 [確定] 按鈕。 此元件名稱會用為命名空間的名稱，因此您可能會想要使用舊專案的命名空間名稱。 這需要您從舊專案將專案建立在與不同的資料夾中。 若選擇不同的名稱，可以在產生的程式碼檔案中，更新命名空間的名稱。

1. 關閉專案。

1. 從您的 Windows 8.1 元件，將所有程式碼檔案 (.cpp、.h、.xaml 等) 複製到新建立的專案。 請勿複製 Package.appxmanifest 檔案。

1. 建置並解決任何起因於 Windows SDK 不同版本間之重大變更的錯誤。

## <a name="troubleshooting"></a>疑難排解

在將程式碼移植到 UWP 的過程中，可能會遇到多種問題。 以下是一些可能會遇到的問題。

### <a name="project-configuration-issues"></a>專案組態問題

您可能會收到下列錯誤：

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

如果發生這種情況，就不會將專案建置為 Windows 通用專案。 請檢查此專案檔，並確定它具有正確的 XML 項目，且它會將專案識別為 Windows 的通用專案。 下列項目應會出現 (目標平台的版本號碼可能會不同)：

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

若是使用 Visual Studio 建立新的 UWP 專案，應不會出現此錯誤。

## <a name="see-also"></a>另請參閱

[Visual C++ 移植指南](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[開發適用於通用 Windows 平台 (UWP) 的應用程式](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)