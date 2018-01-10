---
title: "-INCLUDE （強制符號參考） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs: C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8caf060d278e7ac2c92c38ad58e9c4c55eab632c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="include-force-symbol-references"></a>/INCLUDE (強制符號參考)
```  
/INCLUDE:symbol  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `symbol`  
 指定要加入至符號表的符號。  
  
## <a name="remarks"></a>備註  
 /INCLUDE 選項會告訴連結器將指定的符號加入至符號表。  
  
 若要指定多個符號，輸入逗號 （，）、 分號 （;） 或符號名稱之間的空格。 命令列上指定 /INCLUDE:`symbol`一次是針對每個符號。  
  
 連結器解析`symbol`加上包含的程式，符號定義的物件。 此功能十分有用，包括程式庫物件，否則就不會將連結的程式。  
  
 指定符號使用此選項會覆寫該符號的移除[/opt: ref](../../build/reference/opt-optimizations.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**輸入**屬性頁。  
  
4.  修改**強制符號參考**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)