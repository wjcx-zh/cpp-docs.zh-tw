---
title: "-MIDL （指定 MIDL 命令列選項） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs: C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8e842f4cf0f9c52945c04739879d0132eb34171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (指定 MIDL 命令列引數的選項)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `file`  
 其中包含的檔案名稱[MIDL 命令列選項](http://msdn.microsoft.com/library/windows/desktop/aa366839)。  
  
## <a name="remarks"></a>備註  
 必須提供所有選項的 IDL 檔案轉換至 TLB 檔案`file`;連結器的命令列上，無法指定 MIDL 命令列選項。 如果未指定 /MIDL，則會叫用 MIDL 編譯器只 IDL 檔案名稱和任何其他選項。  
  
 此檔案應該包含每行一個 MIDL 命令列選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**內嵌 IDL**屬性頁。  
  
4.  修改**MIDL 命令**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [/IDLOUT （命名 MIDL 輸出檔）](../../build/reference/idlout-name-midl-output-files.md)   
 [/IGNOREIDL （不要將屬性處理至 MIDL）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/TLBOUT （名稱。TLB 檔案）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [建置屬性化程式](../../windows/building-an-attributed-program.md)