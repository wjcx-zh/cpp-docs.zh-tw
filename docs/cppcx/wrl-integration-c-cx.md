---
title: WRL 整合 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ddefed444c447fbfd300a656c36be45899177b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090256"
---
# <a name="wrl-integration-ccx"></a>WRL 整合 (C++/CX)

自由可以混合使用 WRL 程式碼[!INCLUDE[cppwrl](includes/cppwrl-md.md)] ([!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]) 程式碼。 在同一個轉譯單位中，您可以使用 WRL 物件控制代碼與宣告的物件 (`^`) 標記法和[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]智慧型指標 (`ComPtr<T>`) 標記法。 不過，您必須手動處理傳回值，和[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]HRESULT 錯誤碼和 WRL 例外狀況。
  
## <a name="includecppwrlshortincludescppwrl-short-mdmd-development"></a>[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] 開發

如需有關撰寫和使用[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]元件，請參閱[Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

### <a name="example"></a>範例

下列程式碼片段示範如何使用 WRL 和[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]取用[!INCLUDE[wrt](includes/wrt-md.md)]類別以及檢查中繼資料檔。

此範例是取自建置 Microsoft 市集應用程式論壇中的程式碼片段。 此程式碼片段的作者提供下列免責聲明和條件：

1. C++ 不提供特定應用程式開發介面以反映 [!INCLUDE[wrt](includes/wrt-md.md)] 類型，但 Windows 的類型中繼資料檔 (.winmd) 完全遵循 CLR 中繼資料檔。 Windows 對於取得指定類型的 .winmd 檔案，提供新的中繼資料探索應用程式開發介面 (RoGetMetaDataFile)。 不過，這些應用程式開發介面對於 C++ 開發人員的用途有限，因為您無法具現化類別。

1. 在編譯程式碼後，您還需要傳遞 Runtimeobject.lib 和 Rometadata.lib 至連結器。

1. 這個程式碼片段依現狀供應， 應該可以正確運作，但也可能包含錯誤。

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}

```

## <a name="see-also"></a>另請參閱

[與其他語言間的互通性](interoperating-with-other-languages-c-cx.md)  
