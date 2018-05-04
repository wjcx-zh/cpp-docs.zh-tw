---
title: / /FILEALIGN （檔案中的對齊區段） |Microsoft 文件
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a737801663a2c7c1e896166291a1635fbbe6c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="filealign-align-sections-in-files"></a>/ /FILEALIGN （檔案中的對齊區段）

**/FILEALIGN**連結器選項可讓您指定的輸出檔中寫入為指定大小的倍數區段的對齊方式。

## <a name="syntax"></a>語法

> __/ FILEALIGN:__*大小*

### <a name="parameters"></a>參數

*size*  
以位元組為單位，必須是 2 的乘冪區段對齊大小。

## <a name="remarks"></a>備註

**/FILEALIGN**選項會使連結器来對齊輸出檔案的多個界限上的每一節*大小*值。 根據預設，連結器不使用固定的對齊方式大小。

**/FILEALIGN**選項可用來讓磁碟使用狀況更有效率，或讓頁面將從磁碟載入更快。 較小的區段大小可能很有用執行針對較小裝置，或保留下載較小的應用程式。 區段記憶體對齊，在磁碟上的不會影響記憶體中的對齊方式。

請使用 [DUMPBIN](dumpbin-reference.md) 來查看輸出檔案中區段的相關資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**命令列**中的 屬性頁**連結器**資料夾。

1. 輸入選項名稱 **/FILEALIGN:** 以及的大小**其他選項**方塊。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)   
[連結器選項](../../build/reference/linker-options.md)