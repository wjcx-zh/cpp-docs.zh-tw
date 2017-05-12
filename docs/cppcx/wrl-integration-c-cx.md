---
title: "WRL 整合 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# WRL 整合 (C++/CX)
您可以將 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 程式碼與 [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)] \([!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)]\) 程式碼自由混合使用。 在同一個轉譯單位中，可以使用以 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 物件的控制代碼 \(`^`\) 標記法宣告的物件，以及以 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 智慧型指標 \(`ComPtr<T>`\) 標記法宣告的物件。 不過，您必須手動處理傳回值、[!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] HRESULT 錯誤碼和 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 例外狀況。  
  
## [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 開發  
 如需撰寫和使用 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 元件的詳細資訊，請參閱 [Windows Runtime C\+\+ Template Library \(WRL\)](~/windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## 範例  
 下列程式碼片段示範以 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 和 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 來使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類別以及檢查中繼資料檔。  
  
 此範例取自[建置 Windows 市集應用程式論壇](http://social.msdn.microsoft.com/Forums/winappswithnativecode/thread/211ef583-db11-4e55-926b-6d9ab53dbdb4)的程式碼片段。 此程式碼片段的作者提供下列免責聲明和條件：  
  
1.  C\+\+ 不提供特定應用程式開發介面以反映 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型，但 Windows 的類型中繼資料檔 \(.winmd\) 完全遵循 CLR 中繼資料檔。 Windows 對於取得指定類型的 .winmd 檔案，提供新的中繼資料探索應用程式開發介面 \(RoGetMetaDataFile\)。 不過，這些應用程式開發介面對於 C\+\+ 開發人員的用途有限，因為您無法具現化類別。  
  
2.  在編譯程式碼後，您還需要傳遞 Runtimeobject.lib 和 Rometadata.lib 至連結器。  
  
3.  這個程式碼片段依現狀供應， 應該可以正確運作，但也可能包含錯誤。  
  
```  
  
#include <hstring.h> #include <cor.h> #include <rometadata.h> #include <rometadataresolution.h> #include <collection.h> namespace ABI_Isolation_Workaround { #include <inspectable.h> #include <WeakReference.h> } using namespace ABI_Isolation_Workaround; #include <wrl/client.h> using namespace Microsoft::WRL; using namespace Windows::Foundation::Collections; IVector<String^>^ GetTypeMethods(Object^); MainPage::MainPage() { InitializeComponent(); Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/"); auto methods = GetTypeMethods(uri); std::wstring strMethods; std::for_each(begin(methods), end(methods), [&strMethods](../standard-library/string.md methodName) { strMethods += methodName->Data(); strMethods += L"\n"; }); wprintf_s(L"%s\n", strMethods.c_str()); } IVector<String^>^ GetTypeMethods(Object^ instance) { HRESULT hr; HSTRING hStringClassName; hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ className = reinterpret_cast<String^>(hStringClassName); ComPtr<IMetaDataDispenserEx> metadataDispenser;ComPtr<IMetaDataImport2> metadataImport;hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf()); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD HSTRING hStringFileName; mdTypeDef typeDefToken; hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ fileName = reinterpret_cast<String^>(hStringFileName); HCORENUM hCorEnum = 0; mdMethodDef methodDefs[2048]; ULONG countMethodDefs = sizeof(methodDefs); hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD wchar_t methodName[1024]; ULONG countMethodName; std::wstring strMethods; Vector<String^>^ retVal = ref new Vector<String^>(); for(int i = 0; i < countMethodDefs; ++i) { countMethodName = sizeof(methodName); hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr); if (SUCCEEDED(hr)) { methodName[ countMethodName ] = 0; retVal->Append(ref new String(methodName)); } } return retVal; }  
  
```  
  
## 請參閱  
 [與其他語言間的互通性](../cppcx/interoperating-with-other-languages-c-cx.md)