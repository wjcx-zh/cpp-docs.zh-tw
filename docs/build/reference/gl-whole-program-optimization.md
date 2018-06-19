---
title: -GL （整個程式最佳化） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce972b6e7254ad7454f8e8799283588f0fdd5270
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376269"
---
# <a name="gl-whole-program-optimization"></a>/GL (整個程式最佳化)
啟用整個程式最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
/GL[-]  
```  
  
## <a name="remarks"></a>備註  
 整個程式最佳化，可讓編譯器在程式中的所有模組上執行最佳化的資訊。 不需要整個程式最佳化，在執行最佳化每個模組 （編譯）。  
  
 整個程式最佳化預設為關閉，且必須明確啟用。 不過，所以也可以明確停用其與 **/GL-**。  
  
 所有模組的相關資訊，則編譯器可以：  
  
-   將暫存器的使用最佳化跨函式界限。  
  
-   工作表現較佳的追蹤中的載入和儲存數允許減少的全域資料的修改。  
  
-   工作表現較佳的追蹤可能的指標所修改的項目集合取值 （dereference），減少載入和儲存的數字。  
  
-   內嵌函式定義於另一個模組，即使模組中函式。  
  
 以產生.obj 檔 **/GL**將無法使用這類連結器公用程式，做為[EDITBIN](../../build/reference/editbin-reference.md)和[DUMPBIN](../../build/reference/dumpbin-reference.md)。  
  
 如果編譯您的程式 **/GL**和[/c](../../build/reference/c-compile-without-linking.md)，您應該使用 /LTCG 連結器選項建立輸出檔。  
  
 [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)不能與 **/GL**  
  
 由所產生的檔案格式的 **/GL**目前版本中可能無法讀取由 Visual c + + 的後續版本。 您應該不寄送與所產生的.obj 檔案所組成的.lib 檔案 **/GL**您願意寄送的所有版本的 Visual c + + 的.lib 檔複本，除非您預期使用者現在和將來使用。  
  
 以產生.obj 檔 **/GL**不應建立.lib 檔案，除非將連結.lib 檔產生在相同電腦上使用先行編譯標頭檔 **/GL** .obj 檔案。 在連結時，將會需要從.obj 檔案的先行編譯標頭檔的資訊。  
  
 如需有關適用於最佳化和整個程式最佳化限制的詳細資訊，請參閱[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  **/GL**會分析可用的引導式的最佳化，請參閱 /LTCG 的也。  在編譯時的特性指引最佳化，而且如果您想排序的特性指引最佳化的函式，您必須編譯[/Gy](../../build/reference/gy-enable-function-level-linking.md)或暗示 /Gy 編譯器選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  請參閱[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)如需有關如何指定詳細 **/GL**開發環境中。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)