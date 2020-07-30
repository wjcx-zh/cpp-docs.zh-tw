---
title: /Zc:forScope (強制 for 迴圈範圍中的一致性)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: b1173ad609a1b2c95d6cf118f4e2d5defeec5b9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234337"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (強制 for 迴圈範圍中的一致性)

用來搭配 Microsoft 擴充功能 ( [/Ze](../../cpp/for-statement-cpp.md) ) 實作[for](za-ze-disable-language-extensions.md)迴圈的標準 C++ 行為。

## <a name="syntax"></a>語法

> **/Zc： forScope**[ **-** ]

## <a name="remarks"></a>備註

標準行為是讓 **`for`** 迴圈的初始化運算式在迴圈之後移出範圍 **`for`** 。 在 **/zc： forScope-** 和[/ze](za-ze-disable-language-extensions.md)底下， **`for`** 迴圈的初始化運算式會維持在範圍內，直到本機範圍結束為止。

**/Zc： forScope**選項預設為開啟。 指定[/permissive-](permissive-standards-conformance.md)選項時， **/zc： forScope**不會受到影響。

**/Zc:forScope-** 選項已遭取代，並將在未來版本中移除。 使用 **/Zc:forScope-** 會產生取代警告 D9035。

下列程式碼會在 **/Ze** 下編譯，而非在 **/Za**下：

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

若您使用 **/Zc:forScope-**，當變數因為前一個範圍中所做的宣告而在範圍內時，會產生警告 C4288 (預設為關閉)。 若要示範這點，請移除範例程式碼中的 `//` 字元，以宣告 `int i`。

您可使用 **conform** pragma 來修改 [/Zc:forScope](../../preprocessor/conform.md) 的執行階段行為。

若在具備現有 .pch 檔的專案中使用 **/Zc:forScope-** ，會產生警告、忽略 **/Zc:forScope-** ，並使用現有的 .pch 檔案繼續編譯。 如果您想要產生新的 .pch 檔案，請使用[/yc （建立先行編譯標頭檔）](yc-create-precompiled-header-file.md)。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **語言**] 屬性頁。

1. 修改 [強制在 For 迴圈範圍中一致] **** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A> ＞。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
[/Za、/Ze （停用語言擴充功能）](za-ze-disable-language-extensions.md)<br/>
