---
title: /FA、 /Fa （清單檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1840d2f2ff7d968fdcc19e2013a89af9cec32d24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378947"
---
# <a name="fa-fa-listing-file"></a>/FA、/Fa (清單檔)
建立清單檔包含組譯程式碼。  
  
## <a name="syntax"></a>語法  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/Fa**_路徑名稱_  
  
## <a name="remarks"></a>備註  
`/FA`編譯器選項產生的組譯工具清單檔案的每一個轉譯單位，在編譯中，通常會對應至 C 或 c + + 原始程式檔。 根據預設，只有組譯工具隨附於清單檔案中，會編碼為 ANSI。 選擇性`c`， `s`，和`u`引數`/FA`控制項是否電腦程式碼或原始程式碼一起列出，組合器的輸出，是否列出會編碼為 utf-8。  
  
根據預設，每個清單檔取得基底名稱與相同原始程式檔，且.asm 副檔名。 當電腦程式碼包含使用`c`選項時，清單檔具有.cod 副檔名。 您可以變更的名稱和副檔名的清單檔和建立使用所在之目錄`/Fa`選項。  

### <a name="fa-arguments"></a>/FA 引數  
無  
只有組譯工具語言包含在清單中。  
  
`c`  
選擇性。 在清單中包含電腦的程式碼。  
  
`s`  
選擇性。 包含在清單中的原始程式碼。  
  
`u` 選擇項。 將清單檔，以 utf-8 格式編碼，並包含位元組順序標記。 根據預設，檔案被編碼為 ANSI。 使用`u`建立清單檔正確地顯示在任何系統上，或如果您使用 Unicode 原始程式碼檔做為編譯器的輸入。  
  
如果兩個`s`和`u`要指定，以及如果的原始程式碼檔使用 Unicode 編碼方式，除了 utf-8，則程式碼檔中的行.asm 可能無法正確顯示。  
  
### <a name="fa-argument"></a>/Fa 引數  
無  
一個*來源*的每個原始程式碼檔編譯過程中建立.asm 檔案。  
  
*檔名*清單檔名為*filename*.asm 會放在目前的目錄。 編譯單一原始程式碼檔案時，這個選項才有效。  
  
*filename.extension*  
清單檔名為*filename.extension*放在目前的目錄。 編譯單一原始程式碼檔案時，這個選項才有效。  
  
*目錄*\  
一個*source_file*.asm 檔案會建立並放置於指定*目錄*編譯過程中每個來源的程式碼檔案。 請注意必要尾端有反斜線。 允許只在目前的磁碟上的路徑。  
  
*目錄*\\*filename*清單檔名為*filename*.asm 會放在指定*目錄*。 編譯單一原始程式碼檔案時，這個選項才有效。  
  
*目錄*\\*filename.extension*  
清單檔名為*filename.extension*會放在指定*目錄*。 編譯單一原始程式碼檔案時，這個選項才有效。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  開啟**C/c + +** 資料夾，然後選取**輸出檔**屬性頁。  
  
3.  修改**組合語言輸出**屬性來設定`/FAc`和`/FAs`組譯工具、 電腦及原始程式碼的選項。 修改**使用 Unicode 的組譯工具列出**屬性來設定`/FAu`ANSI 或 utf-8 輸出的選項。 修改**ASM 清單位置**設定`/Fa`選項以列出的檔案名稱和位置。  
  
請注意，同時將**組合語言輸出**和**使用 Unicode 的組譯工具列出**屬性可能會導致[命令列警告 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)。 若要將這些選項在 IDE 中的，使用**其他選項**欄位**命令列**屬性改為頁面。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。 若要指定`/FAu`，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="example"></a>範例  
下列的命令列產生的一個合併的來源和機器程式碼清單稱為 HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>另請參閱  
 [輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)