---
title: / CETCOMPAT （控制流程強制技術相容）
ms.date: 02/01/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 3adb147804674b52a5d77030c48567ec04da6aa6
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703411"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT （控制流程強制技術相容）

指定是否要將標記為相容的控制流程強制技術 (CET) 與可執行映像。

## <a name="syntax"></a>語法

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>引數

**NO**<br/>
指定 executalbe 應該不會標示為與 CET 相容。

## <a name="remarks"></a>備註

控制流程強制技術 (CET) 是電腦處理器的一項功能，可提供防禦惡意軟體攻擊的特定類型的功能。 如需詳細資訊，請參閱 < [Intel 控制流程強制 Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**/CETCOMPAT**連結器選項會告訴連結器將標示為 CET 相容的二進位檔。 **/CETCOMPAT:NO**標示為 CET 與不相容的二進位檔。 如果命令列上指定這兩個選項，則會使用指定的最後一個。 這個參數是目前僅適用於 x86 和 x64 架構。

**/CETCOMPAT**選項是從 Visual Studio 2019 Preview 3 工具組中的。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /CETCOMPAT 連結器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入 **/CETCOMPAT**或 **/CETCOMPAT:NO** ，然後選擇**確定**或**套用**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項並沒有對等的程式設計。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
