---
title: 命令列警告 D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 778830892bca1cbf3520599eb6e918e56bdf17ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196634"
---
# <a name="command-line-warning-d9035"></a>命令列警告 D9035

> 選項 '*option*' 已被取代，將在未來的版本中移除

## <a name="remarks"></a>備註

您指定了編譯器選項，將在未來的編譯器版本中移除。 如果有建議的*選項*取代，此警告後面會接著警告[D9036](../../error-messages/tool-errors/command-line-warning-d9036.md)。

指定的選項仍然可以運作，但您應該立即更新組建設定。 因此，當您升級編譯器時，您的專案較可能會繼續建立。

## <a name="see-also"></a>另請參閱

[已取代和已移除的編譯器選項](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[命令列警告 D9036](command-line-warning-d9036.md)
