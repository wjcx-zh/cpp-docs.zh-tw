---
title: WRL 整合 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: a3c8b824d2cd932a7d284804f3f28781654045e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612117"
---
# <a name="wrl-integration-ccx"></a>WRL 整合 (C++/CX)

自由可以混合 WRL 的程式碼與 Windows 執行階段 c + + 範本庫 (WRL)。 在同一個轉譯單位中，您可以使用宣告使用 WRL 物件控制代碼的物件 (`^`) 標記法和 WRL 智慧型指標 (`ComPtr<T>`) 標記法。 不過，您必須手動處理傳回值和 WRL HRESULT 錯誤碼和 WRL 例外狀況。

## <a name="wrl-development"></a>WRL 開發

如需有關撰寫和使用 WRL 元件的詳細資訊，請參閱 < [Windows 執行階段 c + + 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

### <a name="example"></a>範例

下列程式碼片段示範如何使用 WRL 和 WRL 使用 Windows 執行階段類別，以及檢查中繼資料檔。

此範例是取自建置 Microsoft Store 應用程式論壇中的程式碼片段。 此程式碼片段的作者提供下列免責聲明和條件：

1. C + + 不提供特定的 Api，以反映 Windows 執行階段類型，但類型的 Windows 中繼資料檔 (.winmd) 完全遵循 CLR 中繼資料檔。 Windows 對於取得指定類型的 .winmd 檔案，提供新的中繼資料探索應用程式開發介面 (RoGetMetaDataFile)。 不過，這些應用程式開發介面對於 C++ 開發人員的用途有限，因為您無法具現化類別。

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

[與其他語言交互操作](interoperating-with-other-languages-c-cx.md)
