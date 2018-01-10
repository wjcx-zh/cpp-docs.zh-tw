---
title: "-DEF （指定模組定義檔） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs: C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c35e2c834edd4215c6b2bd671e4fc2ba79262aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="def-specify-module-definition-file"></a>/DEF (指定模組定義檔)
```  
/DEF:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 模組定義檔 (.def) 傳遞至連結器的名稱。  
  
## <a name="remarks"></a>備註  
 /DEF 選項會將模組定義檔 (.def) 傳遞至連結器。 只有一個.def 檔可以指定連結。 如需有關.def 檔的詳細資訊，請參閱[模組定義檔](../../build/reference/module-definition-dot-def-files.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**輸入**屬性頁。  
  
4.  修改**模組定義檔**屬性。  
  
 若要指定.def 檔從開發環境中的，您應該將它加入至專案，以及其他檔案，然後指定 /DEF 選項的檔案。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)