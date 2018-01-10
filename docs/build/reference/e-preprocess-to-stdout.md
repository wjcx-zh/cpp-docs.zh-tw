---
title: "-E （前置處理至 stdout） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /e
dev_langs: C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed083c960421ce17c0ce61036cd05191fc12c797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="e-preprocess-to-stdout"></a>/E (前置處理至 stdout)
前置處理 C 和 c + + 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。  
  
## <a name="syntax"></a>語法  
  
```  
/E  
```  
  
## <a name="remarks"></a>備註  
 此程序中執行所有前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[/C （保留註解在前置處理）](../../build/reference/c-preserve-comments-during-preprocessing.md)以及編譯器選項。  
  
 **/E**新增`#line`的開頭和結尾的每個包含的檔案並移除條件式編譯的前置處理器指示詞的行周圍輸出指示詞。 這些指示詞重新編號前置處理過的檔案所有行。 如此一來，後續的處理階段期間所產生的錯誤是指原始程式檔，而不是前置處理過的檔案中的行號。  
  
 **/E**選項會抑制編譯。 您必須重新提交編譯的前置處理過的檔案。 **/E**也會隱藏輸出檔案從**/FA**， **/Fa**，和**/Fm**選項。 如需詳細資訊，請參閱[/FA、 /Fa （清單檔）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名對應檔）](../../build/reference/fm-name-mapfile.md)。  
  
 若要隱藏`#line`指示詞，使用[/EP （前置處理至 stdout 不 #line 指示詞）](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)選項。  
  
 前置處理過的輸出傳送到檔案而非`stdout`，使用[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項。  
  
 若要隱藏`#line`指示詞，並將傳送至檔案時，前置處理過的輸出使用**/P**和**/EP**一起。  
  
 您無法使用先行編譯標頭與**/E**選項。  
  
 請注意，在前置處理至個別檔案，不會產生空格後權杖。 這可能導致不合法的程式，或有非預期的副作用。 下列程式會編譯成功：  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 不過，如果您使用編譯：  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 `int main`不正確地將會在 test2.cpp `intmain`。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  中，輸入編譯器選項**其他選項**方塊。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>範例  
 下列命令列會前置處理`ADD.C`，保留註解，新增`#line`指示詞，並將結果顯示在標準輸出裝置：  
  
```  
CL /E /C ADD.C  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)