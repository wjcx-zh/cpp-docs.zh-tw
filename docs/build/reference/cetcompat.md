---
title: / CETCOMPAT （CET 陰影堆疊相容）
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356011"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/ CETCOMPAT （CET 陰影堆疊相容）

指定是否要將標記為相容於控制流程強制技術 (CET) 陰影堆疊可執行映像。

## <a name="syntax"></a>語法

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>引數

**NO**<br/>
指定可執行檔應該不會標示為相容於 CET 陰影堆疊。

## <a name="remarks"></a>備註

控制流程強制技術 (CET) 陰影堆疊是提供功能來防範傳回導向程式設計 (ROP) 為基礎的惡意程式碼攻擊的電腦處理器功能。 如需詳細資訊，請參閱 < [Intel 控制流程強制 Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**/CETCOMPAT**連結器選項會告訴連結器將標示為 CET 陰影堆疊相容的二進位檔。 **/CETCOMPAT:NO**標示為 CET 陰影堆疊與不相容的二進位檔。 如果命令列上指定這兩個選項，則會使用指定的最後一個。 這個參數是目前僅適用於 x86 和 x64 架構。

**/CETCOMPAT**選項是從 Visual Studio 2019 Preview 3 工具組中的。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /CETCOMPAT 連結器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入 **/CETCOMPAT**或 **/CETCOMPAT:NO** ，然後選擇**確定**或**套用**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

此選項並沒有對等的程式設計。

## <a name="see-also"></a>另請參閱

[連結器選項](linker-options.md)
