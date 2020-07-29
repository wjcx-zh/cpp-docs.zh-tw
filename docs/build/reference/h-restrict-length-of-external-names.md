---
title: /H (限制外部名稱的長度)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 9a8976700cfb0f333c2715c573aa2d239e2a8e3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218984"
---
# <a name="h-restrict-length-of-external-names"></a>/H (限制外部名稱的長度)

已取代。 限制外部名稱的長度。

## <a name="syntax"></a>語法

> **/H**<em>數位</em>

## <a name="arguments"></a>引數

*number*<br/>
指定程式中允許之外部名稱的最大長度。

## <a name="remarks"></a>備註

根據預設，外部（公用）名稱的長度為2047個字元。 這適用于 C 和 c + + 程式。 使用 **/h**只能減少可允許的識別碼長度上限，而不會增加。 介於 **/h**和*number*之間的空格是選擇性的。

如果套裝程式含的外部名稱長度超過*數位*，則會忽略額外的字元。 如果您編譯不含 **/h**的程式，而且識別碼包含超過2047個字元，編譯器將會產生[嚴重錯誤 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。

長度限制包括任何編譯器建立的前置底線（ **\_** ）或 @ 符號（ **\@** ）。 這些字元是識別碼的一部分，並採用重要的位置。

- 編譯器會將前置底線（ **\_** ）新增至由 **`__cdecl`** （預設）和呼叫慣例所修改的名稱 **`__stdcall`** ，以及呼叫慣例所修改之名稱的前置字元（ **\@** ） **`__fastcall`** 。

- 編譯器會將引數大小資訊附加至由和呼叫慣例所修改的名稱 **`__fastcall`** **`__stdcall`** ，並將類型資訊加入至 c + + 名稱。

您可能會發現 **/h**很有用：

- 當您建立混合語言或便攜程式時。

- 當您使用的工具會限制外部識別碼的長度。

- 當您想要限制符號在 debug 組建中使用的空間量。

下列範例顯示如果識別碼長度限制太多，使用 **/h**實際上可能會引發錯誤：

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

使用 **/h**選項時，您也必須小心，因為預先定義的編譯器識別碼。 如果識別碼的長度上限太小，某些預先定義的識別碼將無法解析，以及特定的程式庫函數呼叫。 例如，如果使用函式， `printf` 而且在編譯時期指定了 **/H5**選項，則會建立符號 **_prin** ，以供參考 `printf` ，而且不會在程式庫中找到。

使用 **/h**與[/Gl （整個程式優化）](gl-whole-program-optimization.md)不相容。

**/H**選項在 Visual Studio 2005 之後已被取代。已增加最大長度限制，已不再需要 **/h** 。 如需已被取代的編譯器選項清單，請參閱[依分類列出的編譯器選項](compiler-options-listed-by-category.md)中**已取代和移除的編譯器選項**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
