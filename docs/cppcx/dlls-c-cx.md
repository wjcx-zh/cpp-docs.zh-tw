---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740264"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

您可以使用 Visual Studio 來建立標準的 Win32 DLL，或可供通用 Windows 平臺（UWP）應用程式使用的 Windows 執行階段元件 DLL。 使用版本 Visual Studio 或早于 Visual Studio 2012 的 Microsoft C++編譯器所建立的標準 DLL 可能無法在 UWP 應用程式中正確載入，且可能無法在 Microsoft Store 中傳遞應用程式驗證測試。

## <a name="windows-runtime-component-dlls"></a>Windows 執行階段元件 Dll

在大多數情況下，當您想要建立 DLL 以用於 UWP 應用程式時，請使用該名稱的專案範本，將它建立為 Windows 執行階段元件。 您可以為具有公用或私用 Windows 執行階段類型的 Dll 建立 Windows 執行階段元件專案。 Windows 執行階段元件可以從以任何 Windows 執行階段相容語言撰寫的應用程式中存取。 根據預設，Windows 執行階段元件專案的編譯器設定會使用 **/ZW**參數。 .winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 DLL 的名稱不需符合 .winmd 檔案名稱。

如需詳細資訊，請參閱 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>在您的專案中參考協力廠商 Windows 執行階段元件二進位檔

1. 針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **一般屬性** ] 頁面上，選擇 [ **加入新參考** ] 按鈕。

1. Windows 執行階段元件是由包含中繼資料的 DLL 檔案和 winmd 檔案所組成。 這些檔案通常位於相同的資料夾中。 在 [ **加入參考** ] 對話方塊的左窗格中選擇 [ **瀏覽** ] 按鈕，然後巡覽至 DLL 及其 .winmd 檔案的所在位置。 如需詳細資訊，請參閱[擴充功能 sdk](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks)。

## <a name="standard-dlls"></a>標準 DLL

您可以為C++不會使用或產生公用 Windows 執行階段類型的程式碼建立標準 DLL，並從 UWP 應用程式取用。 當您只想要在這個版本的 Visual Studio 中遷移現有 DLL 以進行編譯，但不要將程式碼轉換成 Windows 執行階段元件專案時，請使用動態連結程式庫（DLL）專案類型。 當您進行下列步驟時，這個 DLL 將會隨 .appx 封裝中的應用程式可執行檔一起部署。

### <a name="to-create-a-standard-dll-in-visual-studio"></a>在 Visual Studio 中建立標準 DLL

1. 在功能表列上，選擇 **[檔案]、[** **新增**]、[**專案**]，然後選取 [**動態連結程式庫（DLL）** ] 範本。

1. 輸入專案的名稱，然後選擇 [ **確定** ] 按鈕。

1. 新增程式碼。 請確定為您要匯出的函式使用 `__declspec(dllexport)` ，例如 `__declspec(dllexport) Add(int I, in j);`。

1. 新增`#include winapifamily.h`以包含 UWP 應用程式的 Windows SDK 的標頭檔，並設定宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>若要從相同的方案參考標準 DLL 專案

1. 針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **一般屬性** ] 頁面上，選擇 [ **加入新參考** ] 按鈕。

1. 在左窗格中選取 [ **方案**]，然後在右窗格中選取適當的核取方塊。

1. 在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。

### <a name="to-reference-a-standard-dll-binary"></a>若要參考標準 DLL 二進位檔

1. 將 DLL 檔、.lib 檔和標頭檔複製並貼至已知位置，例如您目前的專案資料夾。

1. 針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **組態屬性**]、[ **連結器**]、[ **輸入** ] 頁面上，將 .lib 檔新增為相依性。

1. 在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>遷移現有的適用于 UWP 應用程式相容性的 Win32 DLL

1. 建立 [DLL （通用 Windows）] 類型的專案，並在其中加入現有的原始程式碼。

1. 新增`#include winapifamily.h`以包含 UWP 應用程式的 Windows SDK 的標頭檔，並設定宏`WINAPI_FAMILY=WINAPI_PARTITION_APP`。

1. 在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。
