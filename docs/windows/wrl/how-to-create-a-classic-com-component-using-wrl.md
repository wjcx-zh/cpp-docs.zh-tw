---
title: HOW TO：建立傳統 COM 元件，使用 WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: 918369a6e43dc9cfb81c5f07afc7aa88a663dee3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335698"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>HOW TO：建立傳統 COM 元件，使用 WRL

若要建立基本的傳統 COM 元件，用於桌面應用程式，除了使用通用 Windows 平台 (UWP) 應用程式中，您可以使用 Windows 執行階段 c + + 範本庫 (WRL)。 建立 COM 元件時，Windows 執行階段 c + + 樣板程式庫可能需要比 ATL 少的程式碼 Windows 執行階段 c + + 樣板程式庫支援的 COM 子集詳細資訊，請參閱[Windows 執行階段 c + + 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)。

本文件說明如何使用 Windows 執行階段 c + + 樣板程式庫來建立基本的 COM 元件。 雖然您可以使用最符合您需求的部署機制，這份文件也顯示註冊和使用桌面應用程式之 COM 元件的基本方法。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>若要使用 Windows 執行階段 c + + 樣板程式庫來建立基本的傳統 COM 元件

1. 在 Visual Studio 中建立**空白方案**專案。 將專案命名為，比方說， `WRLClassicCOM`。

2. 新增**Win32 專案**至方案。 將專案命名為，比方說， `CalculatorComponent`。 在 **應用程式設定**索引標籤上，選取**DLL**。

3. 新增**Midl 檔 (.idl)** 檔案加入專案。 將檔案命名為，比方說， `CalculatorComponent.idl`。

4. 將此程式碼加入至 CalculatorComponent.idl：

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. 在 CalculatorComponent.cpp 中定義 `CalculatorComponent` 類別。 `CalculatorComponent`類別繼承自[Microsoft::WRL::RuntimeClass](runtimeclass-class.md)。 [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md)指定的類別衍生自[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)而非[IInspectable](https://msdn.microsoft.com/library/br205821)。 (`IInspectable`僅適用於 Windows 執行階段應用程式元件。)`CoCreatableClass`建立適用於函式這類類別的 factory [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 使用下列的程式碼取代中的程式碼`dllmain.cpp`。 此檔案會定義 DLL 匯出函式。 這些函式使用[Microsoft::WRL::Module](module-class.md)類別來管理模組的 class factory。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 新增**模組定義檔 (.def)** 檔案加入專案。 將檔案命名為，比方說， `CalculatorComponent.def`。 此檔案可將連結器命名為要匯出的函式名稱。

8. 將此程式碼加入至 CalculatorComponent.def：

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. 將 runtimeobject.lib 加入至連結器列。 若要深入了解，請參閱[。Lib 檔作為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>使用桌面應用程式的 COM 元件

1. 使用 Windows 登錄註冊 COM 元件。 若要這樣做，建立登錄項目檔案，將其命名`RegScript.reg`，並新增下列文字。 取代 *\<dll 的路徑 >* DLL 的路徑，例如`C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`。

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

2. 執行 RegScript.reg 或將它新增至您的專案**建置後事件**。 如需詳細資訊，請參閱 <<c0> [ 建置前事件/建置後事件命令列對話方塊](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)。

3. 新增**Win32 主控台應用程式**專案加入方案。 將專案命名為，比方說， `Calculator`。

4. 使用此程式碼取代內容`Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>穩固程式設計

這份文件會使用標準的 COM 函式，來示範，您可以使用 Windows 執行階段 c + + 樣板程式庫來撰寫 COM 元件，並使其可用於任何啟用 COM 的技術。 您也可以如使用 Windows 執行階段 c + + 樣板程式庫類型[Microsoft::WRL::ComPtr](comptr-class.md)在傳統型應用程式管理 COM 和其他物件的存留期。 下列程式碼會使用 Windows 執行階段 c + + 樣板程式庫管理的存留期`ICalculatorComponent`指標。 `CoInitializeWrapper` 類別是 RAII 包裝函式，可保證釋放 COM 程式庫，也可保證 COM 程式庫的存留期超過 `ComPtr` 智慧型指標物件的存留期。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>另請參閱

[Windows 執行階段 C++ 範本庫 (WRL)](windows-runtime-cpp-template-library-wrl.md)