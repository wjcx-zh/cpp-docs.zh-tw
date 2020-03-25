---
title: 當另一個資料表包含資料列的參考時，更新資料行
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 95cddfd5f030c7bd8d1220cf040de4bc5a883226
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209478"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>在其他資料表包含資料列參考時更新資料行

某些提供者可以偵測資料列中的哪些資料行變更，但許多提供者都不能。 因此，當您嘗試更新的資料列有參考時，更新資料行可能會導致錯誤。 若要解決這個問題，請建立個別的存取子，只保留您想要變更的資料行。 將該存取子的數目傳遞給 `SetData`。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
