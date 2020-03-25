---
title: 如何：使用 WRL 建立傳統 COM 元件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: a1507a1a980dfd98a235b7456d73add955c02043
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213911"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>如何：使用 WRL 建立傳統 COM 元件

您可以使用 Windows 執行階段C++範本庫（WRL）來建立基本的傳統 COM 元件，以便在桌面應用程式中使用，以及用於通用 WINDOWS 平臺（UWP）應用程式。 若要建立 COM 元件，Windows 執行階段C++範本庫所需的程式碼可能比 ATL 少。 如需 Windows 執行階段C++範本庫支援之 COM 子集的詳細資訊，請參閱[Windows 執行階段C++範本庫（WRL）](windows-runtime-cpp-template-library-wrl.md)。

本檔說明如何使用 Windows 執行階段C++範本庫來建立基本的 COM 元件。 雖然您可以使用最符合您需求的部署機制，這份文件也顯示註冊和使用桌面應用程式之 COM 元件的基本方法。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>若要使用 Windows 執行階段C++範本庫來建立基本的傳統 COM 元件

1. 在 Visual Studio 中，建立**空白方案**專案。 為專案命名，例如 `WRLClassicCOM`。

2. 將**Win32 專案**新增至方案。 為專案命名，例如 `CalculatorComponent`。 在 [**應用程式設定**] 索引標籤上，選取 [ **DLL**]。

3. 將**Midl 檔案（.idl）** 檔案加入至專案。 將檔案命名為，例如 `CalculatorComponent.idl`。

4. 將此程式碼加入至 CalculatorComponent.idl：

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. 在 CalculatorComponent.cpp 中定義 `CalculatorComponent` 類別。 `CalculatorComponent` 類別繼承自[Microsoft：： WRL：： RuntimeClass](runtimeclass-class.md)。 [Microsoft：： WRL：： RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md)指定類別衍生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ，而不是[IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable)。 （`IInspectable` 僅適用于 Windows 執行階段應用程式元件）。`CoCreatableClass` 會建立可搭配如[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)等函式使用之類別的 factory。

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 使用下列程式碼取代 `dllmain.cpp`中的程式碼。 此檔案會定義 DLL 匯出函式。 這些函式會使用[Microsoft：： WRL：： module](module-class.md)類別來管理模組的 class factory。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 將**模組定義檔案（.def）** 檔案新增至專案。 將檔案命名為，例如 `CalculatorComponent.def`。 此檔案可將連結器命名為要匯出的函式名稱。

8. 將此程式碼加入至 CalculatorComponent.def：

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. 將 runtimeobject.lib 加入至連結器列。 若要瞭解作法，請參閱[。Lib 檔案做為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>使用桌面應用程式的 COM 元件

1. 使用 Windows 登錄註冊 COM 元件。 若要這麼做，請建立註冊專案檔案，將它命名為 `RegScript.reg`，然後新增下列文字。 以 DLL 的路徑取代 *\<dll-path >* ，例如 `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`。

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. 執行 RegScript，或將它新增至您專案的**組建後事件**。 如需詳細資訊，請參閱[預先建立事件/建立後事件命令列對話方塊](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)。

3. 將**Win32 主控台應用程式**專案新增至方案。 為專案命名，例如 `Calculator`。

4. 使用下列程式碼來取代 `Calculator.cpp`的內容：

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>最佳化程式設計

本檔使用標準的 COM 函式來示範，您可以使用C++ Windows 執行階段範本庫來撰寫 com 元件，並將它提供給任何具備 COM 功能的技術。 您也可以在桌面C++應用程式中使用 Windows 執行階段範本程式庫類型（例如[MICROSOFT：： WRL：： ComPtr](comptr-class.md) ）來管理 COM 和其他物件的存留期。 下列程式碼會使用 Windows 執行階段C++範本庫來管理 `ICalculatorComponent` 指標的存留期。 `CoInitializeWrapper` 類別是 RAII 包裝函式，可保證釋放 COM 程式庫，也可保證 COM 程式庫的存留期超過 `ComPtr` 智慧型指標物件的存留期。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)
