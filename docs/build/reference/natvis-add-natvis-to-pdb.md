---
title: /NATVIS （將 Natvis 加入 PDB）
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: e758a49b41a17d805b752947cd1944087c8ff852
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320613"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS （將 Natvis 加入 PDB）

> /NATVIS:*filename*

## <a name="parameters"></a>參數

*filename*<br/>
要加入 PDB 檔案的 Natvis 檔案。 它將.natvis 檔案中的偵錯工具視覺效果內嵌到 PDB 時。

## <a name="remarks"></a>備註

/NATVIS 選項將內嵌的 Natvis 檔案中定義的偵錯工具視覺效果*filename*到 LINK 所產生的 PDB 檔案。 這可讓偵錯工具顯示的視覺效果與將.natvis 檔案分開。 若要將一個以上的 Natvis 檔案內嵌在產生的 PDB 檔案中，您可以使用多個 /NATVIS 選項。

連結會使用不建立 PDB 檔案時，會忽略 /NATVIS [/ 偵錯](debug-generate-debug-info.md)選項。 如需建立和使用.natvis 檔案的資訊，請參閱[Visual Studio 偵錯工具中建立原生物件的自訂檢視](/visualstudio/debugger/create-custom-views-of-native-objects)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **命令列**中的屬性頁面**連結器**資料夾。

1. 新增 /NATVIS 選項，以**其他選項**文字方塊。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項並沒有對等的程式設計。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
