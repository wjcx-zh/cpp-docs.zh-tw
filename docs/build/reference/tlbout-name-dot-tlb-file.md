---
title: "-TLBOUT （名稱。TLB 檔案） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c898121a4ac29cc05022504ebfe33949b44eca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (命名 .TLB 檔)
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *path*  
 .Tlb 檔案建立所在絕對或相對路徑規格。  
  
 *filename*  
 指定由 MIDL 編譯器建立的.tlb 檔的名稱。 假設沒有副檔名。指定*filename*.tlb，如果您想.tlb 副檔名。  
  
## <a name="remarks"></a>備註  
 /TLBOUT 選項會指定的名稱和副檔名的.tlb 檔案。  
  
 MIDL 編譯器時，由呼叫 Visual c + + 連結器連結專案具有[模組](../../windows/module-cpp.md)屬性。  
  
 如果未指定 /TLBOUT，.tlb 檔案會從其名稱[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*。 如果未指定 /IDLOUT，.tlb 檔案則會呼叫 vc70.tlb。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**內嵌 IDL**屬性頁。  
  
4.  修改**類型程式庫**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [/IGNOREIDL （不要將屬性處理至 MIDL）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL （指定 MIDL 命令列選項）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [建置屬性化程式](../../windows/building-an-attributed-program.md)