---
title: "-Gw （最佳化全域資料） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Gw
dev_langs: C++
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5e822bf88091d8124a58f6f462ae7934450b5b7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="gw-optimize-global-data"></a>/Gw (最佳化全域資料)
將全域資料封裝在 COMDAT 區段中以進行最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
/Gw[-]  
```  
  
## <a name="remarks"></a>備註  
 **/Gw**選項讓編譯器將全域資料封裝在個別的 COMDAT 區段中。 根據預設， **/Gw**已關閉，而且您必須明確啟用。 若要明確停用，請使用**/Gw-**。 當同時**/Gw**和[/GL](../../build/reference/gl-whole-program-optimization.md)會啟用，連結器會使用整個程式最佳化，多個目的檔中比較 COMDAT 區段，以排除未參考的全域資料或合併相同唯讀全域資料。 這可以大幅減小產生的二進位可執行檔之大小。  
  
 當您編譯和個別連結時，您可以使用[/opt: ref](../../build/reference/opt-optimizations.md)排除未參考的全域資料物件檔案中使用編譯的可執行檔的連結器選項**/Gw**選項。  
  
 您也可以使用[/opt: icf](../../build/reference/opt-optimizations.md)和[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)連結器選項一起使用的多個目的檔任何相同唯讀全域資料編譯可執行檔中合併**/Gw**選項。  
  
 如需詳細資訊，請參閱[簡介 /Gw 編譯器參數](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx)Visual c + + 團隊部落格上。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  修改**其他選項**屬性，以包括**/Gw** ，然後選擇 **確定**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)