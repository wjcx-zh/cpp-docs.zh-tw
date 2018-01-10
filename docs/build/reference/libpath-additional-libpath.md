---
title: "-LIBPATH (其他 Libpath) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs: C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 452158c2767ec4f0bf30a88df17b7c01496e24e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (其他 Libpath)
```  
/LIBPATH:dir  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `dir`  
 指定的路徑連結器會搜尋再搜尋 LIB 環境選項中指定的路徑。  
  
## <a name="remarks"></a>備註  
 使用 /LIBPATH 選項覆寫環境程式庫路徑。 連結器會先搜尋此選項時，所指定的路徑中，而且再搜尋 LIB 環境變數中指定的路徑。 您可以指定您輸入每個 /LIBPATH 選項只能有一個目錄。 如果您想要指定多個目錄，您必須指定多個 /LIBPATH 選項。 連結器就會搜尋指定的目錄順序。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**其他程式庫目錄**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)