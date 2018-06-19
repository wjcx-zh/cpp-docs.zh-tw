---
title: -NATVIS （加入至 PDB 的 Natvis） |Microsoft 文件
ms.date: 08/10/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3bce34095aec1558d2466447770a8ac4c46528f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377098"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS （加入至 PDB 的 Natvis）
  
> / NATVIS:*檔名*  
  
## <a name="parameters"></a>參數  
  
*filename*  
Natvis 檔案新增至 PDB 檔案。 它在 Natvis 檔案中內嵌偵錯工具視覺化到 PDB 中。  
  
## <a name="remarks"></a>備註  
  
/NATVIS 選項將內嵌的 Natvis 檔案中定義的偵錯工具視覺化*filename*到 LINK 所產生的 PDB 檔案。 這可讓偵錯工具顯示的視覺效果獨立.natvis 檔案。 您可以使用多個 /NATVIS 選項所產生的 PDB 檔案中內嵌一個以上的 Natvis 檔案。  
  
使用未建立 PDB 檔案時，LINK 會忽略 /NATVIS[偵錯](../../build/reference/debug-generate-debug-info.md)選項。 如需建立和使用.natvis 檔案的資訊，請參閱[在 Visual Studio 偵錯工具中建立原生物件的自訂檢視](/visualstudio/debugger/create-custom-views-of-native-objects)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**命令列**中的 屬性頁**連結器**資料夾。  
  
3.  新增 /NATVIS 選項，以**其他選項**文字方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   這個選項不需要以程式設計方式的對等項目。  
  
## <a name="see-also"></a>另請參閱  
  
[在 Visual Studio 偵錯工具中建立原生物件的自訂檢視](/visualstudio/debugger/create-custom-views-of-native-objects)  
[設定連結器選項](../../build/reference/setting-linker-options.md)  
[連結器選項](../../build/reference/linker-options.md)