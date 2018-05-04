---
title: -/Qvec-report （自動向量化工具報告層級） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ddbb68c20ade9f66215d3a60f2db7ea545409a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (自動向量化工具報告層級)
可讓編譯器的報告功能[Auto-vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) ，並在編譯期間指定的層級的資訊訊息輸出。  
  
## <a name="syntax"></a>語法  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>備註  
 **/Qvec-report-: 1**  
 輸出參考用訊息之向量化迴圈。  
  
 **/Qvec-report-: 2**  
 輸出參考用訊息之迴圈已向量化之迴圈的未向量化，連同原因碼。  
  
 如需原因代碼和訊息的資訊，請參閱[向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /Qvec-report 編譯器選項  
  
1.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。  
  
2.  在**屬性頁**對話方塊的  **C/c + +**，選取**命令列**。  
  
3.  在**其他選項**方塊中，輸入`/Qvec-report:1`或`/Qvec-report:2`。  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>以程式設計方式設定 /Qvec-report 編譯器選項  
  
-   請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [原生程式碼以進行平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=263662)