---
title: /Ob (內嵌函式展開)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915475"
---
# <a name="ob-inline-function-expansion"></a>/Ob (內嵌函式展開)

控制函式的內嵌展開。 根據預設, 優化時, 會在編譯器針對所有函式 (通常稱為*自動內嵌*) 進行擴充。

## <a name="syntax"></a>語法

::: moniker range=">=vs-2019"

> **/Ob**{**0** |12| **3**}|

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob**{**0** |12|}

::: moniker-end

## <a name="arguments"></a>引數

**0**\
[/Od](od-disable-debug.md)下的預設值。 停用內嵌展開。

**1**\
只允許展開標記為[inline](../../cpp/inline-functions-cpp.md)、 [__inline](../../cpp/inline-functions-cpp.md)或[__forceinline](../../cpp/inline-functions-cpp.md)的函式, 或在C++類別宣告中定義的成員函式中。

**2**\
[/O1](o1-o2-minimize-size-maximize-speed.md)和[/O2](o1-o2-minimize-size-maximize-speed.md)下的預設值。 允許編譯器擴充未明確標示為不內嵌的任何函式。

::: moniker range=">=vs-2019"

**3**\
此選項指定比 **/Ob2**更積極的內嵌, 但具有相同的限制。 **/Ob3**選項從 Visual Studio 2019 開始提供。

::: moniker-end

## <a name="remarks"></a>備註

編譯器會將內嵌展開選項和關鍵字視為建議， 不保證任何函式都會以內嵌方式展開。 您可以停用內嵌擴充, 但無法強制編譯器內嵌特定的函式, 即使使用`__forceinline`關鍵字也一樣。

若要將函式排除為內嵌展開的候選項目, 您可以使用[__declspec (noinline)](../../cpp/noinline.md), 或標示為[#pragma auto_inline (off)](../../preprocessor/auto-inline.md)和[#pragma auto_inline (on)](../../preprocessor/auto-inline.md)指示詞的區域。 如需將內嵌提示提供給編譯器的另一種方式的詳細資訊, 請參閱[#pragma](../../preprocessor/intrinsic.md)內建指示詞。

> [!NOTE]
> 從分析測試回合所收集的資訊會覆寫因為您指定了 **/Ob**、 **/os**或 **/ot**而生效的優化。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > ] [**C/C++**   > 優化] 屬性頁。

1. 修改**內嵌函數展開**屬性。

::: moniker range=">=vs-2019"

**/Ob3**選項在內嵌函式**展開**屬性中無法使用。 若要設定 **/Ob3**:

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [ > **C/C++**  **命令列**] 屬性頁。

1. 在 [**其他選項**] 中輸入 **/Ob3** 。

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (優化程式碼)](o-options-optimize-code.md)\
[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
