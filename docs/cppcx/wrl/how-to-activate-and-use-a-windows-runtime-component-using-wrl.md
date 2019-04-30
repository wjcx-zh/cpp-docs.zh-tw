---
title: HOW TO：啟用和使用 Windows 執行階段元件使用 WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 8c0bed825f76fdf0f2c5cc1fa095e54f08bb8a67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398351"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>HOW TO：啟用和使用 Windows 執行階段元件使用 WRL

本文件說明如何使用 Windows 執行階段C++範本庫 (WRL) 來初始化 Windows 執行階段，以及如何啟用和使用 Windows 執行階段元件。

若要使用的元件，您必須取得的型別由元件實作的介面指標。 和 Windows 執行階段的基礎技術是元件物件模型 (COM)，因為您必須遵循 COM 規則，以維護型別的執行個體。 例如，您必須維持*參考次數*，決定何時從記憶體中刪除類型。

若要簡化的 Windows 執行階段，Windows 執行階段使用C++範本程式庫提供智慧型指標範本中， [ComPtr\<T >](comptr-class.md)，，會自動執行參考計數。 當您宣告變數時，指定`ComPtr<`*介面名稱*`>` *識別碼*。 若要存取的介面成員，將套用的箭號成員存取運算子 (`->`) 的識別碼。

> [!IMPORTANT]
> 當您呼叫介面函式時，一定要測試的 HRESULT 傳回值。

## <a name="activating-and-using-a-windows-runtime-component"></a>啟用及使用 Windows 執行階段元件

下列步驟使用`Windows::Foundation::IUriRuntimeClass`介面，以示範如何建立啟用 factory 之 Windows 執行階段元件、 建立該元件的執行個體和擷取屬性值。 此外，它們也會示範如何初始化 Windows 執行階段。 完整的範例如下。

> [!IMPORTANT]
> 雖然您通常會使用 Windows 執行階段C++通用 Windows 平台 (UWP) 應用程式，此範例中的範本程式庫會用於圖例中的主控台應用程式。 這類函式`wprintf_s`所沒有的 UWP 應用程式。 如需類型和您可以使用 UWP 應用程式中的函式的詳細資訊，請參閱[通用 Windows 平台應用程式不支援的 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)並[Win32 與 UWP 應用程式的 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>若要啟動與使用 Windows 執行階段元件

1. 包含 (`#include`) 任何所需的 Windows 執行階段，Windows 執行階段C++範本程式庫，或C++標準程式庫標頭。

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   建議您利用`using namespace`在.cpp 檔案中，讓程式碼更容易閱讀的指示詞。

2. 初始化應用程式執行所在的執行緒。 每個應用程式必須初始化其執行緒和執行緒模型。 這個範例會使用[Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md)類別，以初始化 Windows 執行階段，並指定[RO_INIT_MULTITHREADED](/windows/desktop/api/roapi/ne-roapi-ro_init_type)為執行緒模型。 `RoInitializeWrapper`類別會呼叫`Windows::Foundation::Initialize`在建構，和`Windows::Foundation::Uninitialize`何時會終結。

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   在第二個陳述式中， [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult)運算子會傳回`HRESULT`呼叫`Windows::Foundation::Initialize`。

3. 建立*啟動處理站*如`ABI::Windows::Foundation::IUriRuntimeClassFactory`介面。

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows 執行階段會使用完整名稱來識別類型。 `RuntimeClass_Windows_Foundation_Uri`參數是由 Windows 執行階段，並包含必要的執行階段類別名稱的字串。

4. 初始化[Microsoft::WRL::Wrappers::HString](hstring-class.md)變數，以代表 URI `"http://www.microsoft.com"`。

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   在 Windows 執行階段中，您不配置記憶體之 Windows 執行階段會使用字串。 相反地，Windows 執行階段會建立字串的複本中的緩衝區，它會維護和使用進行此作業，並再傳回的控制代碼緩衝區，它會建立。

5. 使用`IUriRuntimeClassFactory::CreateUri`factory 方法可建立`ABI::Windows::Foundation::IUriRuntimeClass`物件。

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. 呼叫`IUriRuntimeClass::get_Domain`方法來擷取的值`Domain`屬性。

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. 列印至主控台的網域名稱，並傳回。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/desktop/api/winstring/nf-winstring-windowsgetstringrawbuffer)函式會擷取基礎 Unicode 格式的 URI 字串。

以下是完整的範例：

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`wrl-consume-component.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)