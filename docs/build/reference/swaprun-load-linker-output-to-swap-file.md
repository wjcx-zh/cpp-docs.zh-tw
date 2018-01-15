---
title: "-SWAPRUN （連結器輸出載入至交換檔） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs: C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3b6829a20e80ab8548460205169e1cd258694e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (將連結器輸出載入至交換檔)
```  
/SWAPRUN:{NET|CD}  
```  
  
## <a name="remarks"></a>備註  
 /SWAPRUN 選項會告訴作業系統在第一次複製連結器輸出到交換檔，然後從該處執行映像。 這是 Windows NT 4.0 （和更新版本） 功能。  
  
 如果指定 NET，作業系統會先二進位映像從網路複製到交換檔，並載入從該處。 此選項可用於透過網路執行應用程式。 指定 CD 時，作業系統就會卸除式磁碟的映像複製到分頁檔，並再載入它。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**系統**屬性頁。  
  
4.  修改下列屬性的其中一個：  
  
    -   **從光碟片交換執行**  
  
    -   **從網路交換執行**  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 屬性。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)