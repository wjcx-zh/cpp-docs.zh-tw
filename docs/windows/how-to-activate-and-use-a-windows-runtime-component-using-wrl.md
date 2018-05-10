---
title: 如何： 啟用和使用 Windows 執行階段元件使用 WRL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50c37438bf3a840f57119245b845d0b94f1873db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>如何：利用 WRL 啟動與使用 Windows 執行階段元件
本文件示範如何初始化 Windows 執行階段使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 以及如何啟用和使用 Windows 執行階段元件。  
  
 若要使用的元件，您必須取得的類型由該元件實作的介面指標。 和 Windows 執行階段的基礎技術是元件物件模型 (COM)，因為您必須遵循 COM 規則，以維護類型的執行個體。 例如，您必須維護*參考計數*，決定何時從記憶體中刪除類型。  
  
 若要簡化的 Windows 執行階段使用，Windows 執行階段 c + + 樣板程式庫提供的智慧型指標範本， [ComPtr\<T >](../windows/comptr-class.md)，自動執行參考計數。 當您宣告變數時，指定`ComPtr<`*介面名稱*`>` *識別碼*。 若要存取介面成員，套用箭號成員存取運算子 (`->`) 識別項。  
  
> [!IMPORTANT]
>  當您呼叫介面函式時，一定要測試`HRESULT`傳回值。  
  
## <a name="activating-and-using-a-windows-runtime-component"></a>啟用及使用 Windows 執行階段元件  
 下列步驟會使用`Windows::Foundation::IUriRuntimeClass`介面，以示範如何建立 Windows 執行階段元件的啟動處理站，建立該元件的執行個體，和擷取屬性值。 它們也會顯示如何初始化 Windows 執行階段。 完整的範例如下。  
  
> [!IMPORTANT]
>  雖然您通常會使用 Windows 執行階段 c + + 樣板程式庫，在通用 Windows 平台 (UWP) 應用程式中，此範例會使用主控台應用程式的圖例。 函式，如`wprintf_s`所沒有的 UWP 應用程式。 如需型別和函式，您可以在 UWP 應用程式中使用的詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)和[Win32 和 COM 用於 UWP 應用程式](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。  
  
#### <a name="to-activate-and-use-a-windows-runtime-component"></a>若要啟用和使用 Windows 執行階段元件  
  
1.  包含 (`#include`) 任何必要的 Windows 執行階段、 Windows 執行階段 c + + 樣板程式庫或 c + + 標準程式庫標頭。  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     我們建議您利用`using namespace`指示詞在.cpp 檔案中，讓程式碼更容易閱讀。  
  
2.  初始化應用程式執行所在的執行緒。 每個應用程式必須初始化其執行緒和執行緒模型。 這個範例會使用[Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md)初始化 Windows 執行階段類別，並指定[RO_INIT_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx)為執行緒模型。 `RoInitializeWrapper`類別會呼叫`Windows::Foundation::Initialize`在建構，以及`Windows::Foundation::Uninitialize`被終結時。  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     在第二個陳述式中， [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md)運算子會傳回`HRESULT`呼叫`Windows::Foundation::Initialize`。  
  
3.  建立*啟用 factory*如`ABI::Windows::Foundation::IUriRuntimeClassFactory`介面。  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     Windows 執行階段會使用完整限定名稱來識別類型。 `RuntimeClass_Windows_Foundation_Uri`參數是由 Windows 執行階段提供，而且包含必要的執行階段類別名稱的字串。  
  
4.  初始化[Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md)表示 URI 變數`"http://www.microsoft.com"`。  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     在 Windows 執行階段中，您不會使用 Windows 執行階段的字串配置記憶體。 相反地，Windows 執行階段會建立在緩衝區中，會維護和會使用執行作業，並再將控制代碼傳回至緩衝區，它會建立一份您的字串。  
  
5.  使用`IUriRuntimeClassFactory::CreateUri`factory 方法來建立`ABI::Windows::Foundation::IUriRuntimeClass`物件。  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  呼叫`IUriRuntimeClass::get_Domain`方法來擷取的值`Domain`屬性。  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  列印到主控台的網域名稱，並傳回。 所有`ComPtr`和 RAII 物件離開範圍，且會自動釋放。  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx)函式會擷取基礎 Unicode 格式的 URI 字串。  
  
 以下是完整的範例：  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`wrl-consume-component.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe wrl 取用 component.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>另請參閱  
 [Windows 執行階段 C++ 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)