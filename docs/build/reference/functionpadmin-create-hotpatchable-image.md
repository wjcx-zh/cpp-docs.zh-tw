---
title: /FUNCTIONPADMIN (建立可線上修補的影像)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818618"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (建立可線上修補的影像)

準備映像進行 hotpatch。

## <a name="syntax"></a>語法

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>引數

*space*<br/>
若要新增到以位元組為單位的每個函式的開頭的填補量。 在 x86 上預設為 5 個位元組的填補，x64 上預設為 6 個位元組。 在其他目標上必須提供值。

## <a name="remarks"></a>備註

為了讓連結器產生的可進行 hotpatch 的映像，.obj 檔中必須已以編譯[/hotpatch （建立可線上修補的影像）](hotpatch-create-hotpatchable-image.md)。

當您編譯和連結的映像，cl.exe，單一引動過程 **/hotpatch**意味著 **/functionpadmin**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 請輸入 **/FUNCTIONPADMIN**選項**其他選項**。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
