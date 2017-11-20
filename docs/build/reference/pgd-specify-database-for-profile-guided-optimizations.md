---
title: "-PGD （指定特性指引最佳化的資料庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs: C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37113ef23adbbb50e36b51ed8ef0035ee20e885e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (指定特性指引最佳化資訊庫)
/PGD:`filename`  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `filename`  
 指定將用來儲存執行計畫的相關資訊的.pgd 檔的名稱。  
  
## <a name="remarks"></a>備註  
 當使用[/ltcg: pginstrument](../../build/reference/ltcg-link-time-code-generation.md)，用於 /PGD 為.pgd 檔指定非預設名稱或位置。 如果您未指定 /PGD，.pgd 檔案名稱會做為輸出檔 （.exe 或.dll） 名稱相同，並將從中連結已叫用的相同目錄中建立。  
  
 當使用 /ltcg: pgoptimize，使用 /PGD 來指定要用來建立最佳化映像的.pgd 檔的名稱。  
  
 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**最佳化**屬性頁。  
  
5.  修改**特性指引資料庫**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)