---
title: -D （前置處理器定義） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
dev_langs:
- C++
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b8b386d55804421fb6cb454b4818db52e7cea85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376594"
---
# <a name="d-preprocessor-definitions"></a>/D (前置處理器定義)
為原始程式檔定義前置處理符號。  
  
## <a name="syntax"></a>語法  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## <a name="remarks"></a>備註  
 您可以搭配 `#if` 或 `#ifdef` 使用此符號，條件式編譯原始程式碼。 在程式碼中重新定義符號定義或者以 `#undef` 指示詞取消定義之前，符號定義都會保持有效。  
  
 **/D**具有相同的效果`#define`指示詞的原始程式碼檔案中，不同處在於開頭 **/D**去除命令列上的引號和`#define`會保留。  
  
 與符號相關聯的值預設為 1。 例如， **/D** `name`相當於 **/D**`name`**= 1**。 在本文中，定義的結尾處範例**測試**示範用來列印`1`。  
  
 編譯使用 **/D** `name` **=** 造成符號沒有相關聯的值。 雖然仍可使用該符號對程式碼進行條件式編譯，但除此以外，毫無意義。 在範例中，如果您使用編譯 **/DTEST =**，就會發生錯誤。 這個行為與使用包含或不含某值的 `#define` 相似。  
  
 此命令會定義 TEST.c 中的符號 DEBUG：  
  
 **CL /DDEBUG 測試。C**  
  
 此命令會移除 TEST.c 中所有出現的關鍵字 `__far`：  
  
 **CL /D__far = TEST。C**  
  
 **CL**環境變數不能設定為字串，包含等號。 若要使用 **/D**搭配**CL**環境變數，您必須指定數字的符號，而不是等號：  
  
```  
SET CL=/DTEST#0  
```  
  
 在命令提示字元定義前置處理符號時，請考慮編譯器剖析規則及殼層剖析規則。 例如，若要在您的程式中定義百分比前置處理符號 (%)，請在命令提示字元指定兩個百分比符號字元 (%%)：如果您只指定一個，則會發出剖析錯誤。  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，選取**組態屬性**， **C/c + +**，**前置處理器**。  
  
3.  在右窗格中，右邊的資料行的中**前置處理器定義**屬性中，開啟下拉式選單，然後選擇 **編輯**。  
  
4.  在**前置處理器定義**對話方塊中，加入 （每行一個）、 修改或刪除一個或多個定義。 選擇**確定**以儲存變更。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。  
  
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
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/U、 /u （取消定義符號）](../../build/reference/u-u-undefine-symbols.md)   
 [#undef 指示詞 （C/c + +）](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)