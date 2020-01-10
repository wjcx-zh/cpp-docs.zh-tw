---
title: /D (前置處理器定義)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: b10d611d38508f5696dd3b72fb8458e9b61082c8
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230402"
---
# <a name="d-preprocessor-definitions"></a>/D (前置處理器定義)

為原始程式檔定義前置處理符號。

## <a name="syntax"></a>語法

> **/D** ]名稱 | [`=` [{ | 字串*編號*}]] \ `#` \[
> **/D** \[ ]名稱 [[{`=`字串編號 | }]] |  `"` `#``"`

## <a name="remarks"></a>備註

您可以搭配 `#if` 或 `#ifdef` 使用此符號，條件式編譯原始程式碼。 符號定義會持續有效，直到在程式`#undef`代碼中重新定義為止，或指示詞未在程式碼中定義。

**/D**與原始程式碼檔案開頭的指示`#define`詞具有相同的效果。 差別在於 **/d**會在命令列上去除引號，而`#define`指示詞會保留它們。 **/D**與符號之間可以有空白字元。 符號和等號之間不得有空白字元，或是在等號與指派的任何值之間不能有空格。

與符號相關聯的值預設為 1。 例如，`/D name` 等於 `/D name=1`。 在本文結尾的範例中， `TEST`會顯示的定義以進行列印。 `1`

使用`/D name=`進行編譯時，符號*名稱*不會有相關聯的值。 雖然仍可使用該符號對程式碼進行條件式編譯，但除此以外，毫無意義。 在範例中，如果您使用 `/DTEST=` 進行編譯，便會發生錯誤。 這個行為與使用包含或不含某值的 `#define` 相似。

**/D**選項不支援類似函數的巨集定義。 若要插入無法在命令列上定義的定義，請考慮[/fi （命名強制包含檔案）](fi-name-forced-include-file.md)編譯器選項。

您可以在命令列上使用 **/d**多次來定義其他符號。 如果相同的符號定義了一次以上，則會使用最後一個定義。

此命令會定義 TEST.c 中的符號 DEBUG：

```cmd
CL /DDEBUG TEST.C
```

此命令會移除 TEST.c 中所有出現的關鍵字 `__far`：

```cmd
CL /D __far= TEST.C
```

**CL**環境變數不能設定為包含等號的字串。 若要搭配使用 **/d**與**CL**環境變數，您必須指定數位記號（`#`），而不是等號：

```cmd
SET CL=/DTEST#0
```

在命令提示字元定義前置處理符號時，請考慮編譯器剖析規則及殼層剖析規則。 例如，若要在您的程式中定義百分比-`%`符號前置處理符號（），請在命令提示字元`%%`中指定兩個百分比符號字元（）。 如果您只指定一個，就會發出剖析錯誤。

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在左窗格中選取 [設定] [**屬性**]、[ **CC++/** ]、[**預處理器**]。

1. 在右窗格中，在 [**預處理器定義**] 屬性的右邊資料行中，開啟下拉式功能表，然後選擇 [**編輯**]。

1. 在 [**預處理器定義**] 對話方塊中，加入（每行一個）、修改或刪除一個或多個定義。 選取 [確定] 儲存您的變更。

   您不需要在此處指定的定義上包含 '/D ' 選項前置詞。 在屬性頁中，定義是以分號（`;`）分隔。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。

## <a name="example"></a>範例

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)\
[/FI （命名強制的 include 檔案）](fi-name-forced-include-file.md)\
[/U、/u （取消定義符號）](u-u-undefine-symbols.md)\
[#undef 指示詞 (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
