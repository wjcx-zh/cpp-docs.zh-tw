---
title: "/Zc:throwingNew （假設運算子新會擲回） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- throwingNew
- /Zc:throwingNew
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc29a364e5001fb319017a1bc2fa084514d52f16
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew （假設運算子新會擲回）

當**/Zc:throwingNew**指定選項時，編譯器最佳化呼叫`operator new`略過檢查，傳回 null 指標。 此選項會告知編譯器假設所有連結的實作`operator new`並自訂配置器符合 c + + 標準和配置失敗時擲回。 根據預設，在 Visual Studio，編譯器要以保守模式產生 null 檢查 (**/Zc:throwingNew-**) 這些呼叫，因為使用者可以將連結具有非擲回實作的`operator new`或撰寫自訂配置器常式傳回 null 指標。

## <a name="syntax"></a>語法

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>備註

因為 ISO C + + 98，標準指定預設[運算子 new](../../standard-library/new-operators.md#op_new)會擲回`std::bad_alloc`記憶體配置失敗時。 版本的 Visual c + +，Visual Studio 6.0 最上配置失敗，傳回 null 指標。 在 Visual Studio 2002 中，從`operator new`符合標準，並在失敗時擲回。 若要支援使用較舊的配置樣式程式碼，Visual Studio 提供的連結實作`operator new`中在失敗時傳回 null 指標的 nothrownew.obj 連結。 根據預設，編譯器也會產生防禦 null 檢查，以防止這些較舊樣式的配置器失敗造成立即的損毀。 **/Zc:throwingNew**選項會告訴編譯器將會省略這些 null 檢查，假設所有連結的記憶體配置器符合標準。 這不適用於明確非擲回`operator new`使用其他的型別參數宣告的多載`std::nothrow_t`並有明確的`noexcept`規格。

就概念而言，在可用存放區中建立的物件，則編譯器會產生程式碼，配置其記憶體，然後叫用其建構函式初始化的記憶體。 因為 Visual c + + 編譯器通常無法分辨是否這段程式碼將會連結到不合格，非擲回的配置器，依預設它也會產生 null 的檢查，再呼叫建構函式。 這可防止將 null 指標取值 （dereference) 中的建構函式呼叫非擲回的配置失敗。 在大部分情況下，這些檢查會不必要的因為預設`operator new`配置器會擲回，而不是傳回 null 指標。 檢查也有不幸的副作用。 它們壅塞，而程式碼大小、 它們填滿分支預測工具，而它們影響其他有用的編譯器最佳化，例如 devirtualization 或 const 的傳用超出初始化的物件。 檢查的目的是為了支援程式碼連結至*nothrownew.obj 連結*或具有自訂不合格`operator new`實作。 如果您不使用不合格`operator new`，我們建議您改用**/Zc:throwingNew**最佳化程式碼。

**/Zc:throwingNew**選項預設為關閉，並不會受到[/ 寬鬆-](permissive-standards-conformance.md)選項。

如果您使用連結時間程式碼產生 (LTCG) 編譯，您不需要指定**/Zc:throwingNew**。 當您的程式碼編譯使用 /LTCG 時，編譯器可以偵測如果預設值，不符合`operator new`會使用實作。 若是如此，編譯器省去了 null 檢查自動。 連結器會尋找**/ThrowingNew**旗標，告訴如果實作`operator new`符合。 您可以指定這個旗標給連結器在您自訂運算子的新實作的來源中包含這個指示詞：

```cpp
#pragma comment(linker, "/ThrowingNew")
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 從**組態**下拉式功能表中，選擇 **所有組態**。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/Zc:throwingNew**或**/Zc:throwingNew-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[終止 （例外狀況）](../../standard-library/exception-functions.md#terminate)<br/>
