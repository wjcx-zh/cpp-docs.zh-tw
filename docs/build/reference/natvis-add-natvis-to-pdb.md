---
title: /NATVIS (將 Natvis 新增至 PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: a16e320a2f8f946912fef6a354f27f6514a67e29
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439284"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (將 Natvis 新增至 PDB)

> /NATVIS：*filename*

## <a name="parameters"></a>參數

*filename*<br/>
要加入 PDB 檔案中的 Natvis 檔案。 它會將 Natvis 檔案中的偵錯工具視覺效果內嵌至 PDB。

## <a name="remarks"></a>備註

/NATVIS 選項會將 Natvis 檔*檔案名*中定義的偵錯工具視覺效果內嵌至連結所產生的 PDB 檔案。 這可讓偵錯工具單獨顯示 natvis 檔案的視覺效果。 您可以使用多個/NATVIS 選項，在產生的 PDB 檔案中內嵌一個以上的 Natvis 檔案。

當 PDB 檔案不是使用[/debug](debug-generate-debug-info.md)選項建立時，LINK 會忽略/NATVIS。 如需建立和使用 natvis 檔案的相關資訊，請參閱[在 Visual Studio 偵錯工具中建立原生物件的自訂視圖](/visualstudio/debugger/create-custom-views-of-native-objects)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [**連結器**] 資料夾中的 [**命令列**] 屬性頁。

1. 將 [/NATVIS] 選項新增至 [**其他選項**] 文字方塊。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項沒有程式設計的對等用法。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
