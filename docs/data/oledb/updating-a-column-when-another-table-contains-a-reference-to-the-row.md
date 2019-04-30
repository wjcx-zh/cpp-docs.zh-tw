---
title: 另一個資料表包含資料列參考時更新資料行
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 46de5f54a3ec6525f779a6b55a700429a2a84fef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389069"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>在其他資料表包含資料列參考時更新資料行

某些提供者可以偵測哪些資料行中資料列變更，但許多提供者不能。 如此一來，更新資料行可能會導致發生錯誤時您想要更新的資料列的參考。 若要解決此問題，請建立保存您想要變更的資料行的個別存取子。 傳遞至該存取子數目`SetData`。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)