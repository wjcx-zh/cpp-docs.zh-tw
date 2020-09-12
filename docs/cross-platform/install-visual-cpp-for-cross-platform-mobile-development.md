---
title: 安裝 C++ 的跨平台行動裝置應用程式開發
ms.date: 10/17/2019
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
ms.openlocfilehash: 6a573b0f7ba261b97af9de24e67f733acac0532f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041948"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>安裝 C++ 的跨平台行動裝置應用程式開發

您可以在 Visual Studio 中使用 c + + 來建立 Windows 桌面應用程式、通用 Windows 平臺 (UWP) 應用程式和 Linux 應用程式。 現在，您可以建立適用于 Android 和 iOS 的 c + + 應用程式。 **使用 c + +** 的行動裝置開發工作負載是 Visual Studio 中一組可安裝的元件。 它包含跨平臺 iOS、Android 和 UWP Visual Studio 範本。 工作負載會安裝您快速入門所需的跨平臺工具和 Sdk。 您不需要自行尋找、下載及設定它們。 您可以使用 Visual Studio 中的這些工具來輕鬆建立、編輯、偵錯及測試跨平台專案。

本文說明如何使用 Visual Studio 安裝使用 c + + 開發跨平臺應用程式所需的工具和協力廠商軟體。 如需總覽，請參閱[Visual C++ 跨平臺](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)行動裝置

## <a name="requirements"></a>需求

::: moniker range="vs-2017"

- 如需安裝需求，請參閱 [Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。

   > [!IMPORTANT]
   > 如果您使用的是 Windows 7 或 Windows Server 2008 R2，則可以為 Windows 桌面應用程式、Android Native Activity 應用程式和程式庫，以及適用于 iOS 的應用程式和程式碼程式庫開發程式碼，但不能開發 Windows Store 或 UWP 應用程式。

::: moniker-end
::: moniker range=">=vs-2019"

- 如需安裝需求，請參閱 [Visual Studio 產品系列系統需求](/visualstudio/releases/2019/system-requirements)。

   > [!IMPORTANT]
   > 如果您使用 Windows 7 或 Windows Server 2008 R2，則開發程式碼的對象可包括 Windows 傳統型應用程式、Android Native Activity 應用程式和程式庫，以及適用於 iOS 的應用程式和程式碼程式庫，但不包括 Windows Phone 或 UWP 應用程式。

::: moniker-end

若要建置特定裝置平台的應用程式，有幾個額外的需求：

- Android SDK 隨附的 x86 Android 模擬器在可使用硬體加速的電腦上最有效果，例如 Intel Hardware Accelerated Execution Manager (HAXM) 。 如需詳細資訊，請參閱 [ (hyper-v & HAXM) 的「模擬器效能的硬體加速 ](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows)」。

- 建立 iOS 的程式碼需要 Apple ID、iOS 開發人員計畫帳戶，以及可在 OS X Mavericks (10.9 版) 或更新版本上執行 [Xcode](https://developer.apple.com/xcode/) 10.2 版或更新版本的 Mac 電腦。 如需安裝步驟連結，請參閱[安裝適用於 iOS 的工具](#install-tools-for-ios)。

- Windows Phone 模擬器需要可執行 Hyper-V 的電腦。 您必須先啟用 Windows 中的 HYPER-V 功能，才能安裝和執行模擬器。 如需詳細資訊，請參閱模擬器的[系統需求](/visualstudio/cross-platform/system-requirements-for-the-visual-studio-emulator-for-android)。

## <a name="get-the-tools"></a>取得工具

Visual Studio Community、Professional 及 Enterprise 版本中都有提供「使用 C++ 進行行動開發」。 若要取得 Visual Studio，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) ] 頁面。 從 Visual Studio 2015 開始，即提供跨平台行動裝置應用程式開發工具。

## <a name="install-the-tools"></a>安裝工具

Visual Studio 安裝程式包含 **使用 c + +** 工作負載的行動裝置開發。 此工作負載會在 Visual Studio 中安裝 Android 和 iOS 開發所需的 c + + 語言工具、範本和元件。 其中包含 Android 組建和偵測所需的 GCC 和 Clang 工具組。 工作負載會安裝 Android SDK，以及與 Mac 通訊以進行 iOS 開發的元件。 它也會安裝支援 iOS 和 Android 應用程式開發所需的協力廠商工具和軟體發展工具組。 大多數協力廠商工具是 Android 平台支援所需的開放原始碼軟體。

- 若要建立以 Android 平臺為目標的 c + + 程式碼，需要 (NDK) 、Apache Ant 和 c + + Android 開發工具的 android 原生開發工具組。

  > [!NOTE]
  > Android NDK 中的某些工具不支援檔案路徑和檔案名中的 Unicode 字元。 如果專案或原始程式檔的路徑或檔案名中有 Unicode 字元，專案將無法建立。

- Google Android Emulator 和 Intel Hardware Accelerated Execution Manager (HAXM) 是選擇性的，但建議使用的元件。  (Intel HAXM 驅動程式只適用于 Intel 處理器，而且與某些 Vm （包括 Hyper-v）不相容。 ) 您可以直接在 Android 裝置上進行開發和偵錯工具，但在桌面上使用模擬器來進行調試通常會更容易。

- 需要 c + + iOS 開發工具，才能建立以 iOS 平臺為目標的 c + + 程式碼。

> [!NOTE]
> 如果您使用 Visual Studio 2015，請參閱[安裝適用於跨平台行動裝置應用程式開發的 Visual C++ (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015&preserve-view=true)

### <a name="install-the-mobile-development-with-c-workload"></a>安裝「使用 C++ 進行行動開發」工作負載

1. 從 [開始]**** 功能表執行 [Visual Studio 安裝程式]****。

1. 如果您已經安裝 Visual Studio，請選擇所要修改 Visual Studio 安裝版本的 [修改]**** 按鈕。 否則，請選擇 [安裝]**** 來安裝 Visual Studio。

1. 在 Visual Studio 安裝程式中，選取 [工作負載]**** 索引標籤，然後向下捲動並選取 [使用 C++ 進行行動開發]**** 工作負載。 選取此工作負載時，會一併選取 C++ 開發所需的其他必要元件。 您也可以選擇其他要同時安裝的工作負載和個別元件。 若要建置也將 UWP 作為目標的跨平台程式碼，請選取 [通用 Windows 平台開發]**** 工作負載。

1. 在 [安裝詳細資料]**** 窗格中，展開 [使用 C++ 進行行動開發]****。 在 [選擇性]**** 區段中，您可以選擇額外的 NDK 版本、Google Android Emulator、Intel Hardware Accelerated Execution Manager，以及 IncrediBuild 組建加速工具。

1. 此工作負載預設會包含一或多個 Android SDK 安裝程式元件。 有額外的 Android SDK 版本可供使用。 若要為您的安裝新增一個元件，請選擇 [個別元件]**** 索引標籤，然後向下捲動至 [SDK、程式庫和架構]**** 區段來進行選取。

1. 選擇 [修改]**** 或 [安裝]**** 按鈕來安裝 [使用 C++ 進行行動開發]**** 工作負載，以及所選取的其他工作負載和選用元件。

   安裝完成時，關閉安裝程式，然後重新啟動電腦。 協力廠商元件的部分安裝動作在電腦重新開機之前不會生效。

   > [!IMPORTANT]
   > 您必須重新啟動，確定一切都已正確安裝。

1. 開啟 Visual Studio。

## <a name="install-tools-for-ios"></a>Install tools for iOS

您可以使用 Visual Studio 來編輯、偵測 iOS 程式碼，並將其部署至 iOS 模擬器。 或 iOS 裝置。 由於授許可權制，必須在 Mac 上遠端建立程式碼。 若要使用 Visual Studio 建立並執行 iOS 應用程式，請先在您的 Mac 上安裝及設定遠端代理程式。 如需詳細的安裝指示、必要條件及設定選項，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 如果您不是針對  iOS 進行建置，可以略過此步驟。

## <a name="install-or-update-dependencies-manually"></a>手動安裝或更新相依項目

當您安裝 **使用 c + +** 工作負載的行動裝置開發工作負載時，您不需要安裝所有協力廠商相依性 (或 Visual Studio 2015 Visual C++ 行動裝置開發選項) 。 請使用 [ [安裝工具](#install-the-tools)] 中的步驟，稍後再安裝它們。 Visual Studio 安裝程式會定期更新以安裝最新的協力廠商元件。 您可以使用它來安裝已更新的 Sdk 和 Ndk。 您也可以獨立於 Visual Studio 安裝或更新這些項目。

您可以再次在 Android SDK 目錄中執行 SDK 管理員應用程式，以更新 SDK。 以及安裝選用的工具和其他 API 層級。 除非您使用 [以系統管理員身分執行] **** 執行 SDK Manager 應用程式，否則可能無法安裝更新。 如果您有建置 Android 應用程式的問題，請檢查 SDK Manager 以確認已安裝的 SDK 是否有更新。

若要使用某些 Android SDK 模擬器，您可能需要設定硬體加速。 如需詳細資訊，請參閱 [ (hyper-v & HAXM) 的「模擬器效能的硬體加速 ](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)」。

在大多數情況下，Visual Studio 可以偵測到您已安裝之協力廠商軟體的設定。 它會維護內部環境變數中的安裝路徑。 您可以在 Visual Studio IDE 中覆寫這些跨平台開發工具的預設路徑。

### <a name="to-set-the-paths-for-third-party-tools"></a>若要設定協力廠商工具的路徑

1. 在 [Visual Studio] 功能表列上，選取 [**工具**  >  **選項**]。

1. 在 [選項]**** 對話方塊中，選取 [跨平台]**** > [C++]**** > [Android]****。

   ![Android 工具路徑選項](../cross-platform/media/cppmdd-options-android.png "Android 工具路徑選項")

1. 若要變更工具所使用的路徑，請核取路徑旁的核取方塊，並在文字方塊中編輯資料夾路徑。 您也可以使用瀏覽按鈕 (**...**)，開啟 [選取位置] **** 對話方塊並選擇資料夾。

1. 選擇 [確定] **** ，儲存自訂工具資料夾的位置。

## <a name="see-also"></a>另請參閱

[安裝和設定工具以使用 iOS 建立](install-and-configure-tools-to-build-using-ios.md)\
[Visual C++ 跨平台行動開發](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
