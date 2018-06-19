---
title: 如何： 建立傳統 COM 元件，使用 WRL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00f00b265128ca388a3e9d4eb77631a320fbda81
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880081"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>如何：使用 WRL 建立傳統 COM 元件
您可以使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 來建立基本的傳統 COM 元件，用於桌面應用程式，除了使用通用 Windows 平台 (UWP) 應用程式。 若是建立 COM 元件時，Windows 執行階段 c + + 樣板程式庫可能需要比 ATL 少程式碼 Windows 執行階段 c + + 樣板程式庫支援的 COM 子集詳細資訊，請參閱[Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 本文件說明如何使用 Windows 執行階段 c + + 樣板程式庫來建立基本的 COM 元件。 雖然您可以使用最符合您需求的部署機制，這份文件也顯示註冊和使用桌面應用程式之 COM 元件的基本方法。  
  
### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>若要使用 Windows 執行階段 c + + 樣板程式庫來建立基本的傳統 COM 元件  
  
1.  在 Visual Studio 中建立**空白方案**專案。 為專案命名，例如`WRLClassicCOM`。  
  
2.  新增**Win32 專案**至方案。 為專案命名，例如`CalculatorComponent`。 在**應用程式設定**索引標籤上，選取**DLL**。  
  
3.  新增**Midl 檔 (.idl)** 檔案加入專案中。 為檔案命名，例如`CalculatorComponent.idl`。  
  
4.  將此程式碼加入至 CalculatorComponent.idl：  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  在 CalculatorComponent.cpp 中定義 `CalculatorComponent` 類別。 `CalculatorComponent`類別繼承自[Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md)。 [Microsoft::\<ClassicCom >](../windows/runtimeclassflags-structure.md)指定的類別衍生自[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx)而非[IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx)。 (`IInspectable`僅適用於 Windows 執行階段應用程式元件。)`CoCreatableClass`建立處理站類別，可以搭配函式例如[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx)。  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  使用下列程式碼取代 dllmain.cpp 中的程式碼。 此檔案會定義 DLL 匯出函式。 這些函式使用[Microsoft::WRL::Module](../windows/module-class.md)類別以管理模組的 class factory。  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  新增**模組定義檔 (.def)** 檔案加入專案中。 為檔案命名，例如`CalculatorComponent.def`。 此檔案可將連結器命名為要匯出的函式名稱。  
  
8.  將此程式碼加入至 CalculatorComponent.def：  
  
    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE  
    ```

9. 將 runtimeobject.lib 加入至連結器列。 若要了解作法，請參閱[。Lib 檔案做為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>使用桌面應用程式的 COM 元件  
  
1.  使用 Windows 登錄註冊 COM 元件。 若要這樣做，請建立登錄項目檔案，其命名`RegScript.reg`，並加入下列文字。 取代 *\<dll 的路徑 >* 之 DLL 的路徑，例如`C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`。  
  
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
  
2.  執行 RegScript.reg 或將它加入至您的專案**建置後事件**。 如需詳細資訊，請參閱[建置前事件/建置後事件命令列對話方塊](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)。  
  
3.  新增**Win32 主控台應用程式**專案加入方案。 為專案命名，例如`Calculator`。  
  
4.  使用此程式碼取代 Calculator.cpp 的內容：  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 這份文件會使用標準的 COM 函式示範您可以撰寫 COM 元件，並將其提供給任何啟用 COM 的技術使用 Windows 執行階段 c + + 樣板程式庫。 您可以也使用 Windows 執行階段 c + + 樣板程式庫類型例如[comptr](../windows/comptr-class.md)在桌面應用程式管理 COM 和其他物件的存留期。 下列程式碼會使用 Windows 執行階段 c + + 樣板程式庫管理的存留期`ICalculatorComponent`指標。 `CoInitializeWrapper` 類別是 RAII 包裝函式，可保證釋放 COM 程式庫，也可保證 COM 程式庫的存留期超過 `ComPtr` 智慧型指標物件的存留期。  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)