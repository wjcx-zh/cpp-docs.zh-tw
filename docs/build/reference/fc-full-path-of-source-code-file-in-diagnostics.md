---
title: -FC （診斷中的原始程式碼檔的完整路徑） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a721b6887b6c5c07d96a79b06f05e6d7855250b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373201"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (診斷中的原始程式碼檔之完整路徑)

讓編譯器將顯示的傳遞給編譯器診斷中的原始程式檔完整路徑。

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

不含 **/FC**，診斷文字看起來會像下列診斷文字：

- compiler_option_FC.cpp(5)： 錯誤 C2143： 語法錯誤： 遺漏 ';' 才能 '}'

與 **/FC**，診斷文字看起來會像下列診斷文字：

- c:\test\compiler_option_fc.cpp(5)： 錯誤 C2143： 語法錯誤： 遺漏 ';' 才能 '}'

 **/FC**如果您想要使用時，請參閱檔案名稱的完整路徑，也需要&#95;&#95;檔案&#95;&#95;巨集。 請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)如需有關&#95;&#95;檔案&#95;&#95;。

**/FC**選項會隱含 **/ZI**。 如需有關 **/ZI**，請參閱[/Z7、 /Zi、 /ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

**/FC**輸出以小寫的完整路徑。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **進階**屬性頁。

1. 修改**使用完整路徑**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
