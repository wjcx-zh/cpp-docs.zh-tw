---
title: /D (前置處理器定義)
ms.date: 11/04/2016
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
ms.openlocfilehash: 18bbdb980c63b3c04b432602afb2402c5e2c42e7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812079"
---
# <a name="d-preprocessor-definitions"></a>/D (前置處理器定義)

為原始程式檔定義前置處理符號。

## <a name="syntax"></a>語法

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>備註

您可以搭配 `#if` 或 `#ifdef` 使用此符號，條件式編譯原始程式碼。 在程式碼中重新定義符號定義或者以 `#undef` 指示詞取消定義之前，符號定義都會保持有效。

**/D**具有相同的效果`#define`原始程式碼檔，不同之處在於開頭指示詞 **/D**命令列上會去除引號和`#define`保留它們。

與符號相關聯的值預設為 1。 例如， **/D** `name`相當於 **/D**`name`**= 1**。 在範例中，在本文中，定義的結尾處**測試**示範用來列印`1`。

藉由編譯 **/D** `name` **=** 造成符號沒有相關聯的值。 雖然仍可使用該符號對程式碼進行條件式編譯，但除此以外，毫無意義。 在範例中，如果您使用編譯 **/DTEST =**，就會發生錯誤。 這個行為與使用包含或不含某值的 `#define` 相似。

此命令會定義 TEST.c 中的符號 DEBUG：

**CL /DDEBUG 測試。C**

此命令會移除 TEST.c 中所有出現的關鍵字 `__far`：

**CL /D__far=  TEST.C**

**CL**環境變數不能設為字串，包含等號。 若要使用 **/D**連同**CL**環境變數，您必須指定數字的符號，而不是等號：

```
SET CL=/DTEST#0
```

在命令提示字元定義前置處理符號時，請考慮編譯器剖析規則及殼層剖析規則。 例如，若要定義百分比前置處理符號 （%）在程式中，指定兩個百分比符號字元 （%）在命令提示字元中：如果您指定只有一個，就會發出剖析錯誤。

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在左窗格中，選取**組態屬性**， **C/c + +**，**前置處理器**。

1. 在右窗格的右邊資料行**前置處理器定義**屬性，開啟下拉式選單，然後選擇**編輯**。

1. 在 [**前置處理器定義**] 對話方塊中，加入 （每行一個）、 修改或刪除一個或多個定義。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。

## <a name="example"></a>範例

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
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

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
[/U、/u (取消定義符號)](u-u-undefine-symbols.md)<br/>
[#undef 指示詞 (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
