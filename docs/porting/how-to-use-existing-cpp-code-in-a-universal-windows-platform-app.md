---
title: 作法：在通用 Windows 平台應用程式中使用現有的 C++ 程式碼
description: 在通用 Windows 平臺應用程式中使用現有程式碼應用程式和程式庫的方法。
ms.date: 09/04/2020
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: fd23c875d67654e96a828f4dba412dd74652912a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503675"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>作法：在通用 Windows 平台應用程式中使用現有的 C++ 程式碼

有多種方式可讓您使用現有的 c + + 程式碼，通用 Windows 平臺 (UWP) 專案中。 某些方式不需要使用元件延伸模組來重新編譯程式碼 (c + +/CX) 啟用 (也就是 `/ZW` 選項) 和部分用途。 您可能需要保留標準 c + + 中的程式碼，或為一些程式碼保留傳統的 Win32 編譯環境。 您仍然可以使用適當的架構選項來進行。 請考慮所有包含 UWP UI 的程式碼，以及對 c #、Visual Basic 和 JavaScript 呼叫端公開的類型。 這段程式碼應該在 Windows 應用程式專案和 Windows 執行階段元件專案中。 您只從 c + + (（包括 c + +/CX) ）呼叫的程式碼，可以在使用 `/ZW` 選項或標準 c + + 專案編譯的專案中。 不使用不允許之 Api 的純二進位程式碼，可以藉由將它連結為靜態程式庫來使用。 或者，您可以將應用程式封裝成內容，並將它載入 DLL 中。

在 UWP 環境中執行傳統型程式的最簡單方式，可能是使用傳統型橋接器技術。 其中包含 Desktop App Converter，其會將現有應用程式封裝為 UWP 應用程式，而不需要變更程式碼。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

本文的其餘部分將討論如何將 c + + 程式庫 (Dll 和靜態程式庫) 至通用 Windows 平臺。 您可能會想要移植程式碼，讓您的核心 c + + 邏輯可與多個 UWP 應用程式搭配使用。

UWP 應用程式會在受保護的環境中執行。 因此，不允許許多可能會危害平臺安全性的 Win32、COM 和 CRT API 呼叫。 `/ZW`編譯器選項可以偵測到這類呼叫，並產生錯誤。 您可以在應用程式上使用應用程式認證套件，來偵測呼叫不允許之 Api 的程式碼。 如需詳細資訊，請參閱 [Windows 應用程式認證套件](/windows/uwp/debug-test-perf/windows-app-certification-kit)。

如果程式庫可以使用原始程式碼，您可以嘗試消除不允許的 API 呼叫。 如需不允許的 Api 清單，請參閱[通用 Windows 平臺 apps 中不支援](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)UWP 應用程式和 CRT 函式的[Win32 和 COM api](/uwp/win32-and-com/win32-and-com-for-uwp-apps) 。 [UWP 應用程式中的 Windows API 替代方案](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)也提供了幾種替代方案。

如果您只是嘗試將通用 Windows 專案的參考新增至傳統桌面程式庫，您會收到一則錯誤訊息，指出程式庫不相容。 如果是靜態程式庫，您可以連結至程式庫，方法是將程式庫 (檔案 *`.lib`*) 新增至連結器輸入，就像在傳統 Win32 應用程式中的方式一樣。 如果只有二進位程式庫可供使用，它是唯一的選項。 靜態程式庫會連結至應用程式的可執行檔。 不過，您在 UWP 應用程式中使用的 Win32 DLL 必須封裝到應用程式中，方法是將它包含在專案中，並將其標示為內容。 若要在 UWP 應用程式中載入 Win32 DLL，您也必須呼叫， [`LoadPackagedLibrary`](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) 而不是 `LoadLibrary` 或 `LoadLibraryEx` 。

如果您有 DLL 或靜態程式庫的原始程式碼，您可以使用編譯器選項，將它重新編譯為 UWP 專案 `/ZW` 。 然後，您可以使用 **方案總管**來新增對它的參考，然後在 c + + UWP 應用程式中使用它。 使用匯出程式庫連結 DLL。

若要向其他語言的呼叫者公開功能，您可以將程式庫轉換成 Windows 執行階段元件。 Windows 執行階段元件與一般 Dll 不同之處在于，它們包含檔案格式的中繼資料 *`.winmd`* ，這些檔案會以 .net 和 JavaScript 取用者所需的方式來描述內容。  若要向其他語言公開 API 專案，您可以加入 c + +/CX 結構，例如 ref 類別，並將其設為公用。 在 Windows 10 和更新版本中，我們建議 [c + +/WinRT 程式庫](https://github.com/microsoft/cppwinrt) ，而不是 c + +/cx。

上述討論不適用於必須以不同方式處理的 COM 元件。 如果您在 EXE 或 DLL 中有 COM 伺服器，則可以在通用 Windows 專案中使用它。 將其封裝為 [免註冊的 COM 元件](/windows/win32/sbscs/creating-registration-free-com-objects)，將其以內容檔案的形式新增至您的專案，並使用將其具現化 [`CoCreateInstanceFromApp`](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) 。 請參閱 [Using Free-COM DLL in Windows Store C++ Project](/archive/blogs/win8devsupport/using-free-com-dll-in-windows-store-c-project) (在 Microsoft Store C++ 專案中使用 Free-COM DLL)。

如果您想要將現有 COM 程式庫移植到 UWP，也可以將它轉換成 Windows 執行階段元件。 針對這類埠，我們建議使用 c + +/WinRT 程式庫，但您也可以使用 [Windows 執行階段 C++ 範本庫 (WRL) ](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)。 WRL 已被取代，而且不支援 ATL 和 OLE 的所有功能。 這類埠是否可行，取決於您的元件所需的 COM、ATL 和 OLE 功能。

無論您選擇哪一種開發案例，都應該注意一些巨集定義。 您可以在程式碼中使用這些宏，以條件方式在傳統桌面 Win32 和 UWP 下編譯器代碼。

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

這些陳述式分別適用於 UWP 應用程式、Windows Phone Store 應用程式、兩者都適用或兩者均不適用 (僅傳統 Win32 桌面)。 只有 Windows SDK 8.1 和更新版本才提供這些宏。

本文包含下列程式：

- [在 UWP 應用程式中使用 Win32 DLL](#BK_Win32DLL)

- [在 UWP 應用程式中使用原生 c + + 靜態程式庫](#BK_StaticLib)

- [將 c + + 程式庫移植到 Windows 執行階段元件](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a> 在 UWP 應用程式中使用 Win32 DLL

為了提高安全性和可靠性，通用 Windows 應用程式會在受限制的執行時間環境中執行。 在傳統的 Windows 傳統型應用程式中，您不能直接使用任何原生 DLL。 如果您有 DLL 的原始程式碼，就可以移植程式碼，使其在 UWP 上執行。 首先可變更幾個專案設定和專案檔案中繼資料，將該專案識別為 UWP 專案。 您將會使用選項來重新編譯程式庫程式碼 `/ZW` ，而此選項可啟用 c + +/cx。 UWP 應用程式中不允許某些 API 呼叫，因為與該環境相關聯的控制項更嚴格。 如需詳細資訊，請參閱 [適用于 UWP 應用程式的 Win32 和 COM api](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

如果您有使用 `__declspec(dllexport)` 來匯出函式的原生 DLL，您可以將 DLL 重新編譯為 UWP 專案，以從 UWP 應用程式中呼叫這些函式。 例如，假設我們有一個名為 *Giraffe* 的 Win32 DLL 專案，它會匯出幾個類別和其方法，並使用類似下列標頭檔的程式碼：

```cpp
// giraffe.h
// Define GIRAFFE_EXPORTS when building this DLL
#pragma once

#ifdef GIRAFFE_EXPORTS
#define GIRAFFE_API __declspec(dllexport)
#else
#define GIRAFFE_API
#endif

GIRAFFE_API int giraffeFunction();

class Giraffe
{
    int id;
        Giraffe(int id_in);
    friend class GiraffeFactory;

public:
    GIRAFFE_API int GetID();
};

class GiraffeFactory
{
    static int nextID;

public:
    GIRAFFE_API GiraffeFactory();
    GIRAFFE_API static int GetNextID();
    GIRAFFE_API static Giraffe* Create();
};
```

以及下列程式碼：

```cpp
// giraffe.cpp
#include "pch.h"
#include "giraffe.h"

Giraffe::Giraffe(int id_in) : id(id_in)
{
}

int Giraffe::GetID()
{
    return id;
}

int GiraffeFactory::nextID = 0;

GiraffeFactory::GiraffeFactory()
{
    nextID = 0;
}

int GiraffeFactory::GetNextID()
{
    return nextID;
}

Giraffe* GiraffeFactory::Create()
{
    return new Giraffe(nextID++);
}

int giraffeFunction();
```

專案中的其他專案 (*`pch.h`* ， *`dllmain.cpp`*) 是標準 Win32 專案範本的一部分。 程式碼會定義宏 `GIRAFFE_API` ，此宏 `__declspec(dllexport)` 會在定義時解析為 `GIRAFFE_EXPORTS` 。 也就是說，它是在專案建立為 DLL 時定義，而不是在用戶端使用 *`giraffe.h`* 標頭時定義。 此 DLL 可在 UWP 專案中使用，而不需要變更原始程式碼。 只有部分專案設定和屬性需要變更。

當您有使用公開函式的原生 DLL 時，會套用下列程式 `__declspec(dllexport)` 。

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>移植原生 DLL 到 UWP 而不需建立新專案

1. 在 Visual Studio 中開啟 DLL 專案。

1. 開啟 DLL 專案的 [ **專案屬性** ]，並將設定 **設定為 [** **所有**設定]。

1. 在 [專案屬性]**** 中，於 [C/C++]**** > [一般]**** 索引標籤中，將 [使用 Windows 執行階段延伸模組]**** 設定為 [是 (/ZW)]****。 這個屬性會啟用元件延伸 (c + +/CX) 。

1. 在 **方案總管**中，選取專案節點，開啟快捷方式功能表，然後選擇 **[卸載專案**]。 接著，在卸載的專案節點上開啟捷徑功能表，然後選擇要編輯的專案檔。 找出 `WindowsTargetPlatformVersion` 元素，並取代為下列元素。

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   關閉檔案 *`.vcxproj`* ，再開啟快捷方式功能表，然後選擇 [ **重載專案**]。

   **方案總管** 現在會將專案識別為通用 Windows 專案。

1. 請確定先行編譯標頭檔的名稱正確。 在 [先行 **編譯的標頭** ] 區段中，您可能需要將先行 **編譯標頭檔** 從變更 *`pch.h`* 為， *`stdafx.h`* 如果您看到類似下面的錯誤，也可能會發生這種情況：

   > 錯誤 C2857：在 **`/Ycpch.h`** 原始程式檔中找不到使用命令列選項指定的 ' #include ' 語句

   問題是舊版的專案範本對先行編譯標頭檔使用不同的命名慣例。 Visual Studio 2019 和更新版本的專案會使用 *`pch.h`* 。

1. 建置專案。 您可能會收到一些有關命令列選項不相容的錯誤。 例如，現已淘汰但曾頻繁使用的選項 [啟用最少重建 (/Gm)]**** 在許多舊版 C++ 專案中是預設設定，但和 `/ZW` 不相容。

   當您針對通用 Windows 平臺進行編譯時，無法使用某些函數。 您將會看到關於任何問題的編譯器錯誤。 解決這些錯誤，直到您有全新的組建為止。

1. 若要在相同方案中的 uwp 應用程式中使用 DLL，請開啟 uwp 專案節點的快捷方式功能表，然後選擇 [**加入**  >  **參考**]。

   在 [**專案**  >  **方案**] 下，選取 DLL 專案旁的核取方塊，然後選擇 [**確定]** 按鈕。

1. 在 UWP 應用程式的檔案中包含程式庫的標頭檔 (s) *`pch.h`* 。

    ```cpp
    #include "..\Giraffe\giraffe.h"
    ```

1. 如往常般在 UWP 專案中新增程式碼，以叫用函式並從 DLL 中建立型別。

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> 在 UWP 應用程式中使用原生 C++ 靜態程式庫

您可以在 UWP 專案中使用原生 C++ 靜態程式庫，但是要注意一些限制。 請先閱讀[使用 C++/CX 的靜態程式庫](../cppcx/static-libraries-c-cx.md)相關內容。 您可以從 UWP 應用程式存取靜態程式庫中的原生程式碼，但不是建議您在這類靜態程式庫中建立公用 ref 型別。 如果您以 `/ZW` 選項編譯靜態程式庫，管理員 (實際上是偽裝的連結器) 會警告：

> LNK4264: 正在將以 /ZW 編譯的目的檔封存至靜態程式庫；請注意，在撰寫 Windows 執行階段類型時，不建議與包含 Windows 執行階段中繼資料的靜態程式庫連結

不過，您可以在 UWP 應用程式中使用靜態程式庫，而不需要重新編譯它 `/ZW` 。 您的程式庫無法宣告任何 ref 類型或使用 c + +/CX 結構。 但是，如果您的目的只是要使用原生程式碼的程式庫，則可以依照下列步驟執行。

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>若要在 UWP 專案中使用原生 C++ 靜態程式庫

1. 在 UWP 專案的專案屬性中，選擇左窗格中的 [設定**屬性**  >  **連結器**  >  **輸入**]。 在右窗格的 [其他相依性]**** 屬性中，將路徑新增至程式庫。 例如，針對專案中放置其輸出的程式庫 *`<SolutionFolder>\Debug\MyNativeLibrary\MyNativeLibrary.lib`* ，加入相對路徑 *`Debug\MyNativeLibrary\MyNativeLibrary.lib`* 。

1. 新增 include 語句，以將標頭檔參考到您的檔案 *`pch.h`* (如果出現) 或任何檔案中的 *`.cpp`* 必要檔案，然後開始加入使用該程式庫的程式碼。

   ```cpp
   #include "..\MyNativeLibrary\MyNativeLibrary.h"
   ```

   請勿在**方案總管**的 [**參考**] 節點中加入參考。 此機制僅適用於 Windows 執行階段元件。

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> 將 C++ 程式庫移植到 Windows 執行階段元件

假設您想要在 UWP 應用程式中使用靜態程式庫中的原生 Api。 如果您有原生程式庫的原始程式碼，就可以將程式碼移植到 Windows 執行階段元件。 它不再是靜態程式庫;您會將它轉換成可以在任何 c + + UWP 應用程式中使用的 DLL。 此程式描述如何建立使用 c + +/CX 擴充功能的新 Windows 執行階段元件。 如需建立使用 c + +/WinRT 之元件的相關資訊，請參閱 [使用 c + +/WinRT Windows 執行階段元件](/windows/uwp/winrt-components/create-a-windows-runtime-component-in-cppwinrt)。

當您使用 c + +/CX 時，可以加入 ref 型別和其他的 c + +/CX 結構（可供任何 UWP 應用程式程式碼中的用戶端使用）。 您可以從 c #、Visual Basic 或 JavaScript 存取這些類型。 基本程序如下：

- 建立 (通用 Windows) 專案的 Windows 執行階段元件
- 將靜態程式庫的程式碼複製到其中，然後
- 解決由選項所造成的編譯器錯誤 `/ZW` 。

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>若要將 C++ 程式庫移植到 Windows 執行階段元件

1. 建立 (通用 Windows) 專案的 Windows 執行階段元件。

1. 關閉專案。

1. 在 [ **Windows 檔案總管**中，找出新專案。 然後，找出包含您要移植之程式碼的 c + + 程式庫專案。 將原始程式檔 (標頭檔、程式碼檔和其他任何資源（包括從 c + + 程式庫專案) 的子目錄）複製。 將它們貼入新的專案資料夾，並務必保留相同的資料夾結構。

1. 重新開啟 Windows 執行階段元件專案。 在**方案總管**中開啟專案節點的快捷方式功能表，然後選擇 [**加入**  >  **現有專案**]。

1. 從原始專案中選取要新增的所有檔案，然後選擇 **[確定]**。 必要時，對子資料夾重複上述步驟。

1. 您現在已有重複的節點。 如果有一個以上的先行編譯標頭檔 (說， *`stdafx.h`* 和 *`pch.h`*) ，請選擇要保留的一個。 將任何必要的程式碼 (例如 include 陳述式) 複製到您要保留的檔案中。 然後，刪除另一個，並在專案屬性的 [先行 **編譯頭**檔] 底下，確定標頭檔的名稱正確無誤。

   如果您已變更要做為先行編譯標頭使用的檔案，請確定每個檔案的先行編譯標頭檔選項都正確無誤。 依次選取每個檔案 *`.cpp`* ，開啟其 [屬性] 視窗，並確定 [全部] 是設定為 **使用 (/yu) **，除非先行編譯標頭檔應設定為 **建立 (/yc) **。

1. 建置專案，並解決任何錯誤。 這些錯誤可能是使用選項所造成 `/ZW` ，或可能是 Windows SDK 的新版本所造成。 或者，它們可能會反映相依性（例如程式庫相依的標頭檔），或舊專案與新專案之間的專案設定差異。

1. 將公用 ref 型別加入至您的專案，或將一般類型轉換成 ref 型別。 使用這些類型，將進入點公開至您想要從 UWP 應用程式呼叫的功能。

1. 藉由從 UWP 應用程式專案中加入元件的參考來測試該元件，並加入一些程式碼來呼叫您建立的公用 API。

## <a name="see-also"></a>另請參閱

[移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)
