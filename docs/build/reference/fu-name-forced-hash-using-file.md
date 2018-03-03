---
title: "-FU (命名強制 #using 檔案) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17b62859aaf0c9dc6b3313fbb726602b5b83a82c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fu-name-forced-using-file"></a>/FU (命名強制的 #using 檔案)
您可以使用做為傳遞的檔案名稱替代編譯器選項[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)原始程式碼中。  
  
## <a name="syntax"></a>語法  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 指定此編譯中所參考的中繼資料檔案。  
  
## <a name="remarks"></a>備註  
 /FU 參數只接受一個檔名。 若要指定多個檔案，對每一個檔案都要使用 /FU。  
  
 如果您使用[!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)]和參考中繼資料來使用[Friend 組件](../../dotnet/friend-assemblies-cpp.md)功能，您不能使用**/FU**。 您必須在程式碼中使用 `#using` (搭配使用 `[as friend]` 屬性) 來參考中繼資料。 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 中不支援 Friend 組件。  
  
 如需如何建立組件或模組的 common language runtime (CLR) 的資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。 如需有關如何建置資訊[!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]，請參閱[建置應用程式和程式庫](../../cppcx/building-apps-and-libraries-c-cx.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**進階**屬性頁。  
  
4.  修改**強制 #using**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。  
  
## <a name="see-also"></a>請參閱  
 [輸出檔 (/ F) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)