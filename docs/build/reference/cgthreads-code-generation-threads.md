---
title: "-cgthreads （程式碼產生執行緒） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /cgthreads
dev_langs: C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 846e59b0c1303e70e4ed38b43e4869f1f044f64f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (程式碼產生執行緒)
設定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。  
  
## <a name="syntax"></a>語法  
  
```  
/cgthreads[1-8]  
```  
  
## <a name="arguments"></a>引數  
 數字  
 cl.exe 要使用的執行緒數目上限，範圍在 1 到 8 之間。  
  
## <a name="remarks"></a>備註  
 **/Cgthreads**選項會指定 cl.exe 執行緒數目上限會使用以平行方式的最佳化及程式碼產生階段的編譯。 請注意，可能會有之間沒有空格**/cgthreads**和`number`引數。 根據預設，cl.exe 會使用四個執行緒，如同**/cgthreads4**所指定。 如果可以使用更多處理器核心，則較大的 `number` 值可以改善建置時間。 當它結合這個選項會很實用[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 針對建置可以指定多個層級的平行處理原則。 Msbuild.exe 參數**/maxcpucount**指定可以平行執行的 MSBuild 處理序數目。 [/MP （使用多個處理序建置）](../../build/reference/mp-build-with-multiple-processes.md)編譯器旗標會指定 cl.exe 處理程序同時編譯原始程式檔的數目。 **/Cgthreads**選項指定每個 cl.exe 處理序所使用的執行緒數目。 由於處理器可同時執行的執行緒數目最多只能與處理器核心數目相同，因此同時針對所有這些選項指定較大的值不僅沒有什麼用處，反而可能適得其反。 如需如何建置平行專案的詳細資訊，請參閱[建置多個專案，以平行方式](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**組態屬性**， **C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  修改**其他選項**屬性，以包括**/cgthreads**`N`，其中`N`是從 1 到 8 的值，然後選取**確定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)