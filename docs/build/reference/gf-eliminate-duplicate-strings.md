---
title: -GF （消除重複字串） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
dev_langs:
- C++
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2710fe8c5cc444d9e2681620f6813312a1d65a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375889"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (消除重複字串)
可讓編譯器在執行期間在程式映像和記憶體中建立一份完全相同的字串。 這種最佳化稱為*字串共用*，可建立較小的程式。  
  
## <a name="syntax"></a>語法  
  
```  
/GF  
```  
  
## <a name="remarks"></a>備註  
 如果您使用 **/GF**，作業系統不會交換字串的記憶體部分，可以讀取字串回從映像檔。  
  
 **/GF**集區為唯讀的字串。 如果您嘗試修改字串下的 **/GF**，應用程式錯誤，就會發生。  
  
 字串共用，可讓項目做為多個緩衝區的多個指標是多個單一緩衝區的指標。 下列程式碼，`s`和`t`以相同的字串初始化。 字串共用，使其指向相同的記憶體：  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)選項，用於編輯後繼續 」，會自動設定 **/GF**選項。  
  
> [!NOTE]
>  **/GF**編譯器選項會建立每個唯一字串的可定址區段。 而且根據預設，物件檔案可以包含最多 65,536 個可定址區段。 如果您的程式包含超過 65536 的字串，使用[/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)編譯器選項，來建立更多的區段。  
  
 **/GF**是生效時[/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或 **/O2**用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改**啟用字串共用**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)