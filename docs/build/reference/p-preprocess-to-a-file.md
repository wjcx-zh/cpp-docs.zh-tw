---
title: "-P （前置處理至檔案） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs: C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f4de2f19820a846197806e0a24ddc213dd636c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="p-preprocess-to-a-file"></a>/P (前置處理至檔案)
前置處理 C 和 c + + 原始程式檔，並將前置處理過的輸出寫入檔案。  
  
## <a name="syntax"></a>語法  
  
```  
/P  
```  
  
## <a name="remarks"></a>備註  
 檔案具有基底名稱與相同原始程式檔和.i 延伸。 在過程中，會執行所有前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[/C （保留註解在前置處理）](../../build/reference/c-preserve-comments-during-preprocessing.md)選項連同**/P**。  
  
 **/P**新增`#line`指示詞加入輸出中，開頭和結尾的每個包含的檔案以及環繞移除條件式編譯的前置處理器指示詞的行。 這些指示詞重新編號前置處理過的檔案所有行。 如此一來，後續的處理階段期間所產生的錯誤是指原始程式檔，而不是前置處理過的檔案中的行號。 若要抑制產生`#line`指示詞，使用[/EP （前置處理至 stdout 不 #line 指示詞）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)以及**/P**。  
  
 **/P**選項會抑制編譯。 它不會產生.obj 檔案，即使您使用[/Fo （目的檔名稱）](../../build/reference/fo-object-file-name.md)。 您必須重新提交編譯的前置處理過的檔案。 **/P**也會隱藏輸出檔案從**/FA**， **/Fa**，和**/Fm**選項。 如需詳細資訊，請參閱[/FA、 /Fa （清單檔）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名對應檔）](../../build/reference/fm-name-mapfile.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**前置處理器**屬性頁。  
  
4.  修改**產生前置處理過的檔案**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>範例  
 下列命令列會前置處理`ADD.C`，保留註解，新增`#line`指示詞，並將結果寫入至檔案， `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/Fi （前置處理輸出檔名稱）](../../build/reference/fi-preprocess-output-file-name.md)