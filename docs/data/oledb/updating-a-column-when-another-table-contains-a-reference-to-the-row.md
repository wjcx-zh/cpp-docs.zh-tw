---
title: 另一個資料表包含資料列參考時更新資料行 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7998897c80e392326213324804c1809656e051f3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071819"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>在其他資料表包含資料列參考時更新資料行

某些提供者可以偵測哪些資料行中資料列變更，但許多提供者不能。 如此一來，更新資料行可能會導致發生錯誤時您想要更新的資料列的參考。 若要解決此問題，請建立保存您想要變更的資料行的個別存取子。 傳遞至該存取子數目`SetData`。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)