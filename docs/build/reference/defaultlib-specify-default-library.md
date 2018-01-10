---
title: "-DEFAULTLIB （指定預設程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs: C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40fe07543dd9dc65d93cc9f79504f5fd324204dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (指定預設程式庫)
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *程式庫*  
 解析外部參考時，搜尋程式庫的名稱。  
  
## <a name="remarks"></a>備註  
 /DEFAULTLIB 選項加入*文件庫*連結搜尋時解析參考的程式庫的清單。 /DEFAULTLIB 使用指定的程式庫中搜尋命令列上，以及名為.obj 檔中的預設程式庫之前，所指定程式庫之後。  
  
 [忽略所有預設程式庫](../../build/reference/nodefaultlib-ignore-libraries.md)(/ NODEFAULTLIB) 選項會覆寫 /DEFAULTLIB:*文件庫*。 [忽略程式庫](../../build/reference/nodefaultlib-ignore-libraries.md)(/ /NODEFAULTLIB:*文件庫*) 選項會覆寫 /DEFAULTLIB:*文件庫*時相同*文件庫*名稱中同時指定。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
-   無法從 Visual Studio 開發環境中使用這個連結器選項。 若要加入連結階段程式庫，請使用**其他相依性**屬性從**輸入**屬性頁。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)