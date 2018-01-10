---
title: "-Gm （啟用最少重建） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs: C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bc9ff065de2b83d50b6fa905fcc6d1123dbe829
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (啟用最少重建)
啟用最少重建，其可判定是否需要重新編譯包含已變更 C++ 類別定義 (儲存於標頭 (.h) 檔) 的 C++ 原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```  
/Gm  
```  
  
## <a name="remarks"></a>備註  
 編譯器在第一次編譯期間，會在專案的 .idb 檔中，儲存原始程式檔與類別定義之間的相依性資訊  （相依性資訊會告訴哪一個原始程式檔會相依於哪些類別定義，而哪個.h 檔案定義位於）。後續的編譯會使用.idb 檔中儲存的資訊來判斷是否在原始程式檔需要重新編譯，即使它包含修改過的.h 檔案。  
  
> [!NOTE]
>  最少重建依賴於包含檔之間未變更的類別定義。 對於專案來說，類別定義必須是全域的 (給定類別應該只有一個定義)，這是因為 .idb 檔中的相依性資訊是針對整個專案建立的。 如果專案中類別具有多個定義，請停用最少重建。  
  
 因為 incremental 連結器不支援使用.obj 檔案中包含的 Windows 中繼資料[/ZW （Windows 執行階段編譯）](../../build/reference/zw-windows-runtime-compilation.md)選項， **/Gm**選項與不相容**/ZW**。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改**啟用最少重建**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)