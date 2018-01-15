---
title: "-/Qpar （自動平行化工具） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs: C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 073c906e7ecdfcf933e4b91cbcf8d6a77324df76
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (自動平行化工具)
可讓[Auto-parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md)編譯器自動平行化迴圈程式碼中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>備註  
 當編譯器自動平行化程式碼中的迴圈時，它會將計算分散到多個處理器核心。 只有在編譯器判斷這是合法的做法，且平行處理會改善效能時，才會進行迴圈平行化。  
  
 `#pragma loop()` 指示詞可以協助最佳化平行處理特定的迴圈。 如需詳細資訊，請參閱[迴圈](../../preprocessor/loop.md)。  
  
 如需如何啟用自動平行化工具的輸出訊息的資訊，請參閱[/qpar （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)。  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /Qpar 編譯器選項  
  
1.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。  
  
2.  在**屬性頁**對話方塊的  **C/c + +**，選取**命令列**。  
  
3.  在**其他選項**方塊中，輸入`/Qpar`。  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>若要以程式設計方式設定 /Qpar 編譯器選項  
  
-   請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。  
  
## <a name="see-also"></a>請參閱  
 [/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)   
 [/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [#pragma loop （)](../../preprocessor/loop.md)   
 [原生程式碼以進行平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=263662)