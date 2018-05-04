---
title: '-EP （前置處理至 stdout 不 #line 指示詞） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38047fecbbd1bbaa87db3766b046efa8b446d93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (前置處理至 stdout 不加 #line 指示詞)
前置處理 C 和 c + + 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。  
  
## <a name="syntax"></a>語法  
  
```  
/EP  
```  
  
## <a name="remarks"></a>備註  
 在過程中，會執行所有前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[/C （保留註解在前置處理）](../../build/reference/c-preserve-comments-during-preprocessing.md)選項與 **/EP**。  
  
 **/EP**選項會抑制編譯。 您必須重新提交編譯的前置處理過的檔案。 **/EP**也會隱藏輸出檔案從 **/FA**， **/Fa**，和 **/Fm**選項。 如需詳細資訊，請參閱[/FA、 /Fa （清單檔）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名對應檔）](../../build/reference/fm-name-mapfile.md)。  
  
 前置處理過的檔案，而不是原始程式檔的行號，請參閱後續階段中處理期間產生錯誤。 如果您想要參考原始程式檔行號，請使用[/E （前置處理至 stdout）](../../build/reference/e-preprocess-to-stdout.md)改為。 **/E**選項會增加`#line`指示詞，可針對此用途的輸出。  
  
 前置處理過的輸出，傳送與`#line`指示詞檔案中，使用[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項。  
  
 使用將前置處理過的輸出傳送至 stdout，`#line`指示詞，使用 **/P**和 **/EP**在一起。  
  
 您無法使用先行編譯標頭與 **/EP**選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**前置處理器**屬性頁。  
  
4.  修改**產生前置處理過的檔案**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>範例  
 下列命令列前置處理檔`ADD.C`、 保留註解，並將結果顯示在標準輸出裝置：  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)