---
title: -/WINMDDELAYSIGN （部分簽署 winmd） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c50480fae1f4f3e7421236615d059a642d1074f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375554"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (部分簽署 winmd)
可讓部分簽章的 Windows 執行階段中繼資料 (.winmd) 檔案將公開金鑰放在檔案中。  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>備註  
 類似於[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)套用的.winmd 檔案的連結器選項。 使用 **/WINMDDELAYSIGN**如果您想要將僅將公開金鑰放在.winmd 檔案。 根據預設，連結器的作用如同 **/winmddelaysign: no**指定; 也就是說，不會簽署 winmd 檔案。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**Windows 中繼資料**屬性頁。  
  
4.  在**Windows 中繼資料延遲簽署**下拉式清單方塊中，選取您想要的選項。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)