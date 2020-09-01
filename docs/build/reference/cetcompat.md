---
title: '/CETCOMPAT (CET 陰影堆疊相容) '
ms.date: 09/01/2020
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 7de7c2007c29769cb3ac8f89d07de8b00bf44c26
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281819"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (CET 陰影堆疊相容) 

指定是否要將可執行映射標示為與控制流程強制技術相容 (CET) 陰影堆疊。

## <a name="syntax"></a>語法

> **`/CETCOMPAT`**\
> **`/CETCOMPAT:NO`**

## <a name="arguments"></a>引數

**`NO`**<br/>
指定可執行檔不應標示為與 CET 陰影堆疊相容。

## <a name="remarks"></a>備註

控制流程強制技術 (CET) 陰影堆疊是一種電腦處理器功能，可提供防止傳回導向程式設計的功能， (ROP) 的惡意程式碼攻擊。 如需詳細資訊，請參閱 [Intel 控制流程強制技術預覽](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**`/CETCOMPAT`** 連結器選項會指示連結器將二進位檔標示為 CET 陰影堆疊相容。 **`/CETCOMPAT:NO`** 將二進位檔標示為與 CET 陰影堆疊不相容。 如果在命令列上指定這兩個選項，則會使用指定的最後一個選項。 此參數目前僅適用于 x86 和 x64 架構。

**`/CETCOMPAT`** 從 Visual Studio 2019 開始，可以使用此選項。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>若要 `/CETCOMPAT` 在 Visual Studio 中設定連結器選項

從 Visual Studio 2019 16.7 版開始：

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../working-with-project-properties.md)。

1. 選取設定**屬性**  >  **連結器**[  >  **Advanced** ] 屬性頁。

1. 選取 [ **CET 陰影堆疊相容** ] 屬性。

1. 在下拉式清單控制項中，選擇 **`Yes (/CETCOMPAT)`** 將二進位檔標示為 CET 陰影堆疊相容，或 **`No (/CETCOMPAT:NO)`** 將它標示為不相容。

在舊版的 Visual Studio 2019 中：

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**  >  **命令列**] 屬性頁。

1. 在 [ **其他選項** ] 編輯控制項中，加入 *`/CETCOMPAT`* 以將二進位檔標示為 CET 陰影堆疊相容，或明確地將 *`/CETCOMPAT:NO`* 它標示為不相容。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

此選項沒有程式設計對等專案。

## <a name="see-also"></a>另請參閱

[連結器選項](linker-options.md)
