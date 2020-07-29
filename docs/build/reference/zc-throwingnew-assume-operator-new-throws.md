---
title: /Zc:throwingNew (假設擲回運算子 new)
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
ms.openlocfilehash: 7593107a280995145d252efa76e0a88bddbd2275
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211862"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (假設擲回運算子 new)

當您指定 **/zc： throwingNew**選項時，編譯器會將對的呼叫優化， `operator new` 以略過檢查是否有 null 指標傳回。 此選項會告知編譯器假設和自訂配置器的所有連結的執行都 `operator new` 符合 c + + 標準，並在配置失敗時擲回。 根據預設，在 Visual Studio 中，編譯器搭配保守模式會針對這些呼叫產生 null 檢查（**/zc： throwingNew-**），因為使用者可以連結到非擲回的執行， `operator new` 或撰寫會傳回 null 指標的自訂配置器常式。

## <a name="syntax"></a>語法

> **/Zc： throwingNew**[ **-** ]

## <a name="remarks"></a>備註

自 ISO c + + 98 起，標準已指定預設[運算子 new](../../standard-library/new-operators.md#op_new) `std::bad_alloc` 會在記憶體配置失敗時擲回。 Visual Studio 6.0 的 Visual C++ 版本，在配置失敗時傳回 null 指標。 從 Visual Studio 2002 開始， `operator new` 符合標準，並會在失敗時擲回。 為了支援使用較舊配置樣式的程式碼，Visual Studio 在 nothrownew.obj 中提供可連結的執行 `operator new` ，以在失敗時傳回 null 指標。 根據預設，編譯器也會產生防禦性 null 檢查，以防止這些舊版的配置器導致失敗時立即損毀。 **/Zc： throwingNew**選項會指示編譯器省略這些 null 檢查，假設所有連結的記憶體配置器符合標準。 這不會套用至明確的非擲回 `operator new` 多載，而是使用類型的其他參數來宣告， `std::nothrow_t` 而且具有明確的 **`noexcept`** 規格。

在概念上，若要在免費存放區上建立物件，編譯器會產生程式碼來配置其記憶體，然後叫用其函式來初始化記憶體。 由於 MSVC 編譯器通常無法判斷此程式碼是否會連結至不符合規範的非擲回配置器，因此根據預設，在呼叫此函式之前，它也會產生 null 檢查。 這可避免在不擲回配置失敗時，在函式呼叫中進行 null 指標取值。 在大部分情況下，這些檢查是不必要的，因為預設配置器會擲回， `operator new` 而不是傳回 null 指標。 這些檢查也會產生不幸的副作用。 它們會膨脹程式碼大小、將分支預測項淹沒，而且它們會抑制其他有用的編譯器優化，例如 devirtualization 或 const 傳播外的初始化物件。 這些檢查僅支援連結至*nothrownew.obj*的程式碼，或具有自訂不符合規範的執行 `operator new` 。 如果您不使用不符合規範 `operator new` ，建議您使用 **/Zc： throwingNew**來優化您的程式碼。

**/Zc： throwingNew**選項預設為關閉，且不會受到[/permissive-](permissive-standards-conformance.md)選項的影響。

如果您使用連結時產生程式碼（LTCG）進行編譯，則不需要指定 **/zc： throwingNew**。 當您的程式碼使用 LTCG 編譯時，編譯器可以偵測是否使用預設且符合規範的 `operator new` 執行。 若是如此，編譯器會自動保留 null 檢查。 連結器會尋找 **/ThrowingNew**旗標，以判斷的執行 `operator new` 是否符合規範。 您可以藉由在自訂運算子的 [新執行] 的來源中包含這個指示詞，將此旗標指定給連結器：

```cpp
#pragma comment(linker, "/ThrowingNew")
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 從 [**設定**] 下拉式功能表中，選擇 [**所有**設定]。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc： throwingNew**或 **/zc： ThrowingNew** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/Zc (一致性)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[終止（例外狀況）](../../standard-library/exception-functions.md#terminate)<br/>
