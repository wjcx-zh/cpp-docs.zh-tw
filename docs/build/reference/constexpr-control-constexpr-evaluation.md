---
title: /constexpr (控制 constexpr 評估)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 7b3ae1cd732fe1ec234e2734ea4c6fa86db9d5af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223859"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (控制 constexpr 評估)

使用 **/constexpr**編譯器選項，可 **`constexpr`** 在編譯時期控制用於評估的參數。

## <a name="syntax"></a>語法

> **/constexpr：深度**<em>N</em>\
> **/constexpr： backtrace**<em>N</em>\
> **/constexpr：步驟**<em>N</em>

## <a name="arguments"></a>引數

**深度**<em>n</em>會將遞迴函式呼叫的深度限制 **`constexpr`** 為*N*個層級。 預設值為 512。

**backtrace**<em>n</em>在診斷中顯示最多*N* **`constexpr`** 個評估。 預設值為 10。

**步驟**<em>n</em> **`constexpr`** 在執行*n*個步驟之後終止評估。 預設值為100000。

## <a name="remarks"></a>備註

**/Constexpr**編譯器選項會控制運算式的編譯時間評估 **`constexpr`** 。 評估步驟、遞迴層級和 backtrace 深度會受到控制，以防止編譯器花太多時間進行 **`constexpr`** 評估。 如需 language 元素的詳細資訊 **`constexpr`** ，請參閱[Constexpr （c + +）](../../cpp/constexpr-cpp.md)。

從 Visual Studio 2015 開始提供 **/constexpr**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。

2. 在 [設定**屬性**] 底下，展開 [ **C/c + +** ] 資料夾，然後選擇 [**命令列**] 屬性頁。

3. 在 [**其他選項**] 方塊中，輸入任何 **/constexpr**編譯器選項。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
