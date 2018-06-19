---
title: /FUNCTIONPADMIN （建立可線上修補的映像） |Microsoft 文件
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a5ecfcc336e198de0adcc2393f740072d70cae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376750"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (建立可線上修補的影像)

準備映像進行 hotpatch。

## <a name="syntax"></a>語法

> **/FUNCTIONPADMIN**[**:**_space_]  

### <a name="arguments"></a>引數

*space*<br/>
若要加入至每個函式，以位元組為單位的開頭的填補量。 在 x86 上就會預設為 5 個位元組填補，並在 x64 上就會預設為 6 個位元組。 在其他目標上必須提供值。

## <a name="remarks"></a>備註

為了讓連結器產生的可線上修補的映像，.obj 檔中必須有已編譯[/hotpatch （建立可線上修補的影像）](../../build/reference/hotpatch-create-hotpatchable-image.md)。

當您編譯和連結 cl.exe，一次引動的映像 **/hotpatch**意味著 **/functionpadmin**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入 **/FUNCTIONPADMIN**選項**其他選項**。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
