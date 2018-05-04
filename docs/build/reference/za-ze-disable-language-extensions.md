---
title: -Za，-Ze （停用語言擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze (停用語言擴充功能)
**/Za**編譯器選項會發出錯誤 ANSI C89 或 ISO C + + 11 與不相容的語言建構的。 **/Ze**編譯器選項，預設會啟用，啟用 Microsoft 擴充功能。  
  
## <a name="syntax"></a>語法  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  **/Ze**選項已被取代，因為它的行為預設為開啟。 我們建議您改用[/Zc （一致性）](../../build/reference/zc-conformance.md)編譯器選項，以控制特定的語言擴充功能。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**一節中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]編譯器提供的功能之外，採用 ANSI C89、 ISO c99 的規定或 ISO c + + 標準指定的數字。 這些功能統稱為 Microsoft 擴充功能對 C 和 c + +。 這些擴充功能可供使用依預設，且無法使用時 **/Za**指定選項。 如需特定的擴充功能的詳細資訊，請參閱[Microsoft 對 C 和 c + + 擴充功能](../../build/reference/microsoft-extensions-to-c-and-cpp.md)。  
  
 我們建議您停用語言擴充功能藉由指定 **/Za**選項，如果您打算移植程式至其他環境。 當 **/Za**指定，則編譯器會將 Microsoft 擴充關鍵字做為簡單的識別項，會停用其他的 Microsoft 擴充功能，並會自動定義`__STDC__`C 程式的預先定義巨集。  
  
 搭配其他編譯器選項 **/Za**可能會影響編譯器確保標準一致性的方式。 例如， **/Za**和[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md)可能會導致浮點類型升級行為不符合 ISO C99 或 C + + 11 標準。  
  
 如需指定特定的符合標準行為的設定方式，請參閱[/Zc](../../build/reference/zc-conformance.md)編譯器選項。  
  
 如需有關一致性問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在瀏覽窗格中，選擇 **組態屬性**， **C/c + +**，**語言**。  
  
3.  修改**停用語言擴充功能**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/Zc (一致性)](../../build/reference/zc-conformance.md)