---
title: -IGNOREIDL (Don&#39;t 至 MIDL 的處理序屬性) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14d32be32f019e55f8bad9cc01199d8dc6ae6301
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373448"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (不要&#39;t 至 MIDL 的處理序屬性)
```  
/IGNOREIDL  
```  
  
## <a name="remarks"></a>備註  
 /IGNOREIDL 選項指定的任何[IDL 屬性](../../windows/idl-attributes.md)來源中的程式碼不應處理至.idl 檔案。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**內嵌 IDL**屬性頁。  
  
4.  修改**忽略內嵌 IDL**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [/IDLOUT （命名 MIDL 輸出檔）](../../build/reference/idlout-name-midl-output-files.md)   
 [/TLBOUT （名稱。TLB 檔案）](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [/MIDL （指定 MIDL 命令列選項）](../../build/reference/midl-specify-midl-command-line-options.md)   
 [建置屬性化程式](../../windows/building-an-attributed-program.md)