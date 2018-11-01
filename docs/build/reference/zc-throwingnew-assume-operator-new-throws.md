---
title: '/Zc: throwingnew （假設擲回運算子 new）'
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 782cb55d30bfb11f55a0074a5c3245dd389323ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561222"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc: throwingnew （假設擲回運算子 new）

當 **/zc: throwingnew**指定選項時，編譯器最佳化呼叫`operator new`略過檢查，傳回 null 指標。 此選項會告知編譯器假設所有連結的實作`operator new`和自訂配置器符合 c + + 標準，而且在配置失敗時擲回。 根據預設，Visual Studio 中，編譯器要以保守模式就會產生 null 檢查 (**/Zc:throwingNew-**) 的這些呼叫，因為使用者可以連結具有非擲回的實作`operator new`或撰寫自訂配置器的常式傳回 null 指標。

## <a name="syntax"></a>語法

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>備註

因為 ISO C + + 98，標準已指定，預設值[new 運算子](../../standard-library/new-operators.md#op_new)就會擲回`std::bad_alloc`當記憶體配置失敗。 Visual Studio 6.0 到 Visual c + + 版本上配置失敗，傳回 null 指標。 從 Visual Studio 2002`operator new`符合標準，並在失敗時擲回。 若要支援使用較舊的配置樣式的程式碼，Visual Studio 提供可連結實作`operator new`中在失敗時傳回 null 指標的 nothrownew.obj 連結。 根據預設，編譯器也會產生防禦性的 null 檢查，以防止這些舊樣式的配置器失敗造成立即的損毀。 **/Zc: throwingnew**選項會告訴編譯器將省略這些 null 檢查，假設所有連結的記憶體配置器符合標準。 這不適用於明確非擲回`operator new`多載，其會使用其他的型別參數宣告`std::nothrow_t`還有明確`noexcept`規格。

就概念而言，若要建立可用的存放區的物件，則編譯器會產生配置其記憶體的程式碼，然後叫用其建構函式初始化的記憶體。 因為 Visual c + + 編譯器通常無法分辨是否此程式碼將會連結到不合格，非擲回的配置器，依預設它也會產生 null 檢查，再呼叫建構函式。 這可防止將 null 指標取值 （dereference) 的建構函式呼叫中如果非擲回的配置失敗。 在大部分情況下，這些檢查是不必要的因為預設`operator new`配置器會擲回，而不是傳回 null 指標。 檢查也會有太妙的副作用。 它們膨脹的程式碼大小、 它們填滿分支預測工具和他們禁止其他有用的編譯器最佳化，例如 devirtualization 或 const 傳播出初始化的物件。 檢查的目的是為了支援程式碼連結至*nothrownew.obj 連結*，或有自訂不合格`operator new`實作。 如果您不要使用不合格`operator new`，我們建議您使用 **/zc: throwingnew**最佳化程式碼。

**/Zc: throwingnew**選項預設為關閉，並不會受到[/permissive--](permissive-standards-conformance.md)選項。

如果您編譯藉由使用連結時間程式碼產生 (LTCG)，您不需要指定 **/zc: throwingnew**。 當使用 LTCG 編譯您的程式碼時，編譯器可以偵測是否預設值，符合`operator new`會使用實作。 若是如此，編譯器省去了 null 檢查自動。 連結器會尋找 **/ThrowingNew**旗標，告訴如果實作`operator new`符合。 您可以指定此旗標給連結器，此指示詞併入您的新自訂運算子實作的來源：

```cpp
#pragma comment(linker, "/ThrowingNew")
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 從**組態**下拉式功能表中，選擇**所有組態**。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: throwingnew**或是 **/Zc:throwingNew-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[終止 （例外狀況）](../../standard-library/exception-functions.md#terminate)<br/>
