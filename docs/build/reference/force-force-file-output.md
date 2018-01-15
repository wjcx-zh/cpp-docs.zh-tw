---
title: "-FORCE （強制檔案輸出） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs: C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ec19beec52a217df1237de41d0bd81ab447a56d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="force-force-file-output"></a>/FORCE (強制檔案輸出)
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>備註  
 /FORCE 選項會告訴連結器，以建立有效的.exe 檔或 DLL 即使符號參考但未定義或多重定義。  
  
 /FORCE 選項可以接受選擇性引數：  
  
-   使用 /force: multiple 都會建立輸出檔，不論是否連結找到一個以上的符號定義。  
  
-   使用 /FORCE： 無法解析的連結會尋找未定義的符號是否建立輸出檔。 / 強制： 無法解析未解析進入點符號是否會被忽略。  
  
 / 不使用引數的強制表示這兩個多和未解析。  
  
 此選項以建立的檔案可能無法如預期執行。 指定 /FORCE 選項時，連結器會以累加方式連結。  
  
 如果使用編譯的模組**/clr**， **/強制**將不會建立映像。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)