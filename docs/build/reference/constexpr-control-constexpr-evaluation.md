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
ms.openlocfilehash: 4d3f33a64dcebfc40778f81354cb5067a5239ace
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825587"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (控制 constexpr 評估)

在編譯時期，使用 **/constexpr**編譯器選項來控制**constexpr**評估的參數。

## <a name="syntax"></a>語法

> **/constexpr：深度**<em>N</em>\
> **/constexpr： backtrace**<em>N</em>\
> **/constexpr：步驟**<em>N</em>

## <a name="arguments"></a>引數

**深度**<em>n</em>將遞迴**constexpr**函式呼叫的深度限制為*N*個層級。 預設值為 512。

**backtrace**<em>N</em>會在診斷中顯示最多*N*個**constexpr**評估。 預設值為 10。

**步驟**<em>n</em> *步驟之後終止* **constexpr**評估。 預設值為100000。

## <a name="remarks"></a>備註

**/Constexpr**編譯器選項會控制**constexpr**運算式的編譯時間評估。 評估步驟、遞迴層級和 backtrace 深度會受到控制，以防止編譯器在**constexpr**評估上花費太多時間。 如需**constexpr**語言元素的詳細資訊，請參閱[Constexpr （c + +）](../../cpp/constexpr-cpp.md)。

從 Visual Studio 2015 開始提供 **/constexpr**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。

2. 在 [設定**屬性**] 底下，展開 [ **C/c + +** ] 資料夾，然後選擇 [**命令列**] 屬性頁。

3. 在 [**其他選項**] 方塊中，輸入任何 **/constexpr**編譯器選項。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
