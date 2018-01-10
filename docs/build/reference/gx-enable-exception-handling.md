---
title: "-GX （啟用例外狀況處理） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /gx
dev_langs: C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3013b4233621e63de0230e088dfc10ff65a5705d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gx-enable-exception-handling"></a>/GX (啟用例外狀況處理)
已取代。 啟用同步例外狀況處理使用函式假設宣告可透過`extern "C"`絕不會擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
/GX  
```  
  
## <a name="remarks"></a>備註  
 **/GX**已被取代。 使用對等[/EHsc](../../build/reference/eh-exception-handling-model.md)選項。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**一節中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
 根據預設， **/EHsc**，相當於**/GX**，是使用 Visual Studio 開發環境進行編譯時作用中。 使用命令列工具時，指定沒有例外狀況處理。 這就相當於**/GX-**。  
  
 如需詳細資訊，請參閱[c + + 例外狀況處理](../../cpp/cpp-exception-handling.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在瀏覽窗格中，選擇 **組態屬性**， **C/c + +**，**命令列**。  
  
3.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)