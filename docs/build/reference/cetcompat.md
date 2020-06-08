---
title: /CETCOMPAT （CET 陰影堆疊相容）
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421296"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT （CET 陰影堆疊相容）

指定是否要將可執行映射標記為與控制流程強制技術（CET）陰影堆疊相容。

## <a name="syntax"></a>語法

> **/CETCOMPAT** \[**：否**]

## <a name="arguments"></a>引數

**不**<br/>
指定可執行檔不應標記為與 CET 陰影堆疊相容。

## <a name="remarks"></a>備註

控制流程強制技術（CET）陰影堆疊是一種電腦處理器功能，可提供防禦以傳回導向程式設計（ROP）為基礎的惡意程式碼攻擊的功能。 如需詳細資訊，請參閱[Intel 控制流程強制技術預覽](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**/CETCOMPAT**連結器選項會指示連結器將二進位檔標示為 CET 陰影堆疊相容。 **/CETCOMPAT： NO**會將二進位檔標示為與 CET 陰影堆疊不相容。 如果在命令列上指定這兩個選項，則會使用最後一個指定的。 此參數目前僅適用于 x86 和 x64 架構。

**/CETCOMPAT**選項從 Visual Studio 2019 Preview 3 工具組開始提供。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>若要在 Visual Studio 中設定/CETCOMPAT 連結器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **連結器**] 的 [  >  **Advanced** ] 屬性頁。

1. 選取 [ **CET 陰影堆疊相容**] 屬性。

1. 在下拉式清單控制項中，選擇 **[是] \ （/CETCOMPAT）** 以啟用 EH 接續中繼資料，或選取 [**否] （/CETCOMPAT： No）** 來停用它。


### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

此選項沒有程式設計的對等用法。

## <a name="see-also"></a>另請參閱

[連結器選項](linker-options.md)
