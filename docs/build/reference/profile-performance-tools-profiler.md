---
title: -設定檔 （效能工具分析工具） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15379914b4c4852e3065d1abc03c2ce1b17fb044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (效能工具分析工具)
產生可與效能工具分析工具搭配使用的輸出檔。  
  
## <a name="syntax"></a>語法  
  
```  
/PROFILE  
```  
  
## <a name="remarks"></a>備註  
 / 設定檔表示下列的連結器選項：  
  
-   [/OPT: REF](../../build/reference/opt-optimizations.md)  
  
-   /OPT: NOICF  
  
-   [/INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [/FIXED: NO](../../build/reference/fixed-fixed-base-address.md)  
  
 / 設定檔會使連結器產生的程式映像中的重新配置區段。  重新配置區段可讓分析工具來轉換程式映像，以取得設定檔資料。  
  
 **/ 設定檔**才僅適用於企業 （小組開發） 版本。  如需有關 PREfast 的詳細資訊，請參閱[程式碼分析 C/c + + 概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**進階**屬性頁。  
  
5.  修改**設定檔**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)