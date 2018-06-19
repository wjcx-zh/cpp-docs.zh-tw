---
title: -IDLOUT （命名 MIDL 輸出檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7eeb7af3d19a57b6948f867df87b8d04d0397b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376058"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (命名 MIDL 輸出檔)
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>參數  
 *path*  
 絕對或相對路徑規格。 指定的路徑，會影響.idl 檔案的位置所有其他檔案會放置在專案目錄中。  
  
 *filename*  
 指定 MIDL 編譯器所產生的.idl 檔案名稱。 假設沒有副檔名。指定*filename*.idl，如果您想.idl 副檔名。  
  
## <a name="remarks"></a>備註  
 /IDLOUT 選項會指定的名稱和副檔名的.idl 檔案。  
  
 MIDL 編譯器時，由呼叫 Visual c + + 連結器連結專案具有[模組](../../windows/module-cpp.md)屬性。  
  
 /IDLOUT 也會指定 MIDL 編譯器與相關聯之其他輸出檔的檔案名稱：  
  
-   *檔名*.tlb  
  
-   *檔名*_p.c  
  
-   *檔名*_i.c  
  
-   *檔名*.h  
  
 *檔名*是您傳遞給 /IDLOUT 的參數。 如果[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)會指定.tlb 檔案就會取得其名稱從 /TLBOUT *filename*。  
  
 如果您指定 /IDLOUT 都 /TLBOUT，連結器將建立 vc70.tlb、 vc70.idl、 vc70_p.c、 vc70_i.c 和 vc70.h。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**內嵌 IDL**屬性頁。  
  
4.  修改**合併 IDL 主檔名**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [/IGNOREIDL （不要將屬性處理至 MIDL）](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL （指定 MIDL 命令列選項）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [建置屬性化程式](../../windows/building-an-attributed-program.md)