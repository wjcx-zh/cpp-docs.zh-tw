---
title: "如何：利用 WRL 啟動與使用 Windows 執行階段元件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：利用 WRL 啟動與使用 Windows 執行階段元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此文件顯示如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，以及如何啟用和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。  
  
> [!NOTE]
>  這個範例會啟動一個內建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。  若要了解如何建立可以用類似的方式啟動您的元件，請參閱 [逐步解說：建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)。  
  
 若要使用元件，您必須取得介面指標至由元件所實作的型別。  而且，因為 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的基礎技術是元件物件模型 \(COM\)，您必須遵循 COM 規則維護這個型別的執行個體。  例如，您必須維護判斷型別何時從記憶體刪除的 *參考計數*。  
  
 為了簡化使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]， [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供智慧型指標範本， [ComPtr\<T\>](../windows/comptr-class.md)，自動執行的參考計數。  當您宣告變數時，請指定 `ComPtr<`*interface\-name*`>` *identifier*。  若要存取介面成員，請將套用至箭號成員存取運算子 \(`->`\) 至識別項。  
  
> [!IMPORTANT]
>  當您呼叫介面函式時，請務必測試 `HRESULT` 傳回值。  
  
## 活化和使用的 Windows 執行階段元件  
 下列步驟將示範如何使用 `Windows::Foundation::IUriRuntimeClass` 介面建立 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件的啟用 Factory，建立元件的執行個體，並擷取屬性值。  同時也會說明如何初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  完整的程式碼範例如下所示。  
  
> [!IMPORTANT]
>  雖然您通常會在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] ，這個範例使用主控台應用程式來描述。  例如 `wprintf_s` 函式無法從 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式使用。  如需您可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式中使用的型別和函式的詳細資訊，請參閱 [CRT 函式不支援使用 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM Windows 市集應用程式的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
#### 啟動與使用 Windows 執行階段元件  
  
1.  包含 \(`#include`\) 所有必要的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]或 Standard C\+\+ 程式庫的標頭。  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     建議您利用您的 .cpp 檔中的 `using namespace` 指示詞讓程式碼更容易讀取。  
  
2.  初始化應用程式正在執行的執行緒。  每個應用程式必須使用它的執行緒和執行緒模型。  這個範例會使用 [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) 類別來初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 並指定 [RO\_INIT\_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) 為執行緒模型。  `RoInitializeWrapper` 類別會在建構時呼叫 `Windows::Foundation::Initialize` ，在終結時呼叫 `Windows::Foundation::Uninitialize` 。  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     在第二個陳述式， [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) 運算子傳回從呼叫中 `HRESULT` 至 `Windows::Foundation::Initialize`。  
  
3.  建立 `ABI::Windows::Foundation::IUriRuntimeClassFactory` 介面的啟動 *Factory* 。  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完整名稱以識別型別。  `RuntimeClass_Windows_Foundation_Uri` 參數是由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供和包含所需的執行階段類別名稱的字串。  
  
4.  初始化一 `"http://www.microsoft.com"`URI 的 [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) 變數。  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，您不會配置 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 之字串的記憶體。  相反地， [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 建置在作業維護和使用的緩衝資料的複本，然後將控制代碼傳回給它所建立的緩衝區。  
  
5.  請使用 `IUriRuntimeClassFactory::CreateUri` factory 方法建立 `ABI::Windows::Foundation::IUriRuntimeClass` 物件。  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  呼叫 `IUriRuntimeClass::get_Domain` 方法來擷取 `Domain` 屬性的值。  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  網域名稱列印到主控台並傳回。  所有 `ComPtr` 和 RAII 物件離開範圍並自動釋放。  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) 函式擷取 URI 字串的基本 Unicode 格式。  
  
 這裡有個完整範例:  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## 編譯程式碼  
 若要編譯程式碼，請複製並貼到 Visual Studio 專案或貼在名為 `wrl-consume-component.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令的檔案。  
  
 **cl.exe wrl\-consume\-component.cpp runtimeobject.lib**  
  
## 請參閱  
 [Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)