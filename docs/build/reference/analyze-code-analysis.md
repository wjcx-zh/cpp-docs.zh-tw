---
title: "-分析 （程式碼分析） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba76ddd10866e414d9817f628c7a1aec019964de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="analyze-code-analysis"></a>/analyze (程式碼分析)
啟用程式碼分析和控制選項。  
  
## <a name="syntax"></a>語法  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## <a name="arguments"></a>引數  
 /analyze  
 以預設模式開啟分析。 分析會輸出至**輸出**視窗，就像其他錯誤訊息一樣。 使用**/ 分析-**明確關閉分析。  
  
 /analyze:WX-  
 指定**/analyze: WX-**程式碼分析警告，表示不要視為錯誤當您使用編譯**/WX**。 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../../build/reference/compiler-option-warning-level.md)。  
  
 /analyze:log `filename`  
 詳細的分析器結果會做為 XML 寫入至 `filename` 所指定的檔案。  
  
 /analyze:quiet  
 關閉 分析器輸出至**輸出**視窗。  
  
 /analyze:stacksize `number`  
 `number`參數會搭配這個選項使用指定大小，以位元組為單位的警告之堆疊框架[C6262](/visualstudio/code-quality/c6262)產生。 如果未指定這個參數，則預設的堆疊框架大小為 16KB。  
  
 /analyze:max_paths `number`  
 搭配這個選項使用的 `number` 參數會指定要分析的程式碼路徑數目上限。 如果未指定這個參數，則預設數目為 256。 值越大，執行的檢查就越徹底，但是也可能需要較長的時間進行分析。  
  
 /analyze:only  
 通常，編譯器在執行分析器之後，會產生程式碼並進行更多語法檢查。 **/Analyze： 只有**選項會關閉這個程式碼產生階段; 這可讓分析加快，但不是會產生編譯錯誤和可能已探索的編譯器的程式碼產生階段的警告。 如果程式並不是沒有程式碼產生錯誤，分析結果可能就不可靠，因此，建議您只有在程式碼已通過程式碼產生語法檢查且沒有錯誤的情況下，才使用這個選項。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[程式碼分析 C/c + + 概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[程式碼分析 C/c + + 警告](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**程式碼分析**節點。  
  
4.  選取 [ **一般** ] 屬性頁。  
  
5.  修改一或多個**程式碼分析**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)