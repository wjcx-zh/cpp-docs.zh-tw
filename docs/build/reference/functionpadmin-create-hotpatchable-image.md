---
title: /FUNCTIONPADMIN （建立可線上修補的影像） |Microsoft Docs
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
ms.openlocfilehash: 7a82611c453a96e9247e414d6adb777c07320482
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703985"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (建立可線上修補的影像)

準備映像進行 hotpatch。

## <a name="syntax"></a>語法

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>引數

*space*<br/>
若要新增到以位元組為單位的每個函式的開頭的填補量。 在 x86 上預設為 5 個位元組的填補，x64 上預設為 6 個位元組。 在其他目標上必須提供值。

## <a name="remarks"></a>備註

為了讓連結器產生的可進行 hotpatch 的映像，.obj 檔中必須已以編譯[/hotpatch （建立可線上修補的影像）](../../build/reference/hotpatch-create-hotpatchable-image.md)。

當您編譯和連結的映像，cl.exe，單一引動過程 **/hotpatch**意味著 **/functionpadmin**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 請輸入 **/FUNCTIONPADMIN**選項**其他選項**。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
