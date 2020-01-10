---
title: /NOPDB
description: /NOPDB 選項會讓 DUMPBIN 無法載入及搜尋 PDB 檔案中的符號資訊。
ms.date: 12/04/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 7b0c01e59b52bcec6ddf09416dd6aac9999527a6
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856965"
---
# <a name="nopdb"></a>/NOPDB

告訴 DUMPBIN 不要載入和搜尋程式資料庫（PDB）檔案中的符號資訊。

## <a name="syntax"></a>語法

> **/NOPDB**

## <a name="remarks"></a>備註

根據預設，DUMPBIN 會嘗試載入其目標可執行檔的 PDB 檔案。 DUMPBIN 會使用這項資訊來比對位址與符號名稱。 如果 PDB 檔案很大，或必須從遠端伺服器載入，則此程式可能會很耗時。 **/NOPDB**選項會告訴 DUMPBIN 略過此步驟。 它只會列印可執行檔中可用的位址和符號資訊。

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>若要在 Visual Studio 中設定/NOPDB 連結器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] > **連結器** > [**命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，新增 **/NOPDB**選項。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項沒有程式設計的對等用法。

## <a name="see-also"></a>請參閱

[DUMPBIN 命令列](dumpbin-command-line.md)\
[DUMPBIN 選項](dumpbin-options.md)\
[DUMPBIN 參考](dumpbin-reference.md)
