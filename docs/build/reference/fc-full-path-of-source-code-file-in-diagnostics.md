---
title: /FC (診斷中的原始程式碼檔之完整路徑)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 96809f09efd068b80f04a70d4356c1ceaf5f113c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422477"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (診斷中的原始程式碼檔之完整路徑)

可讓編譯器顯示傳遞至編譯器診斷中原始程式碼檔的完整路徑。

## <a name="syntax"></a>語法

> /FC

## <a name="remarks"></a>備註

請考慮下列程式碼範例：

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

不含 **/FC**，診斷文字看起來會類似以下的診斷文字：

- compiler_option_FC.cpp(5) : error C2143: syntax error : missing ';' before '}'

具有 **/FC**，診斷文字看起來會類似以下的診斷文字：

- c:\test\compiler_option_fc.cpp(5) : error C2143: syntax error : missing ';' before '}'

**/FC**如果您想要使用時，請參閱檔案名稱的完整路徑，也需要&#95;&#95;檔案&#95;&#95;巨集。 請參閱[Predefined Macros](../../preprocessor/predefined-macros.md)如需詳細資訊&#95;&#95;檔案&#95;&#95;。

**/FC**選項所默許 **/ZI**。 如需詳細資訊 **/ZI**，請參閱[/z7，/Zi，/ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

**/FC**輸出以小寫的完整路徑。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **進階**屬性頁。

1. 修改**使用完整路徑**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
