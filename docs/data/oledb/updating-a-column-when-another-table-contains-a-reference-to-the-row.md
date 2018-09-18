---
title: 另一個資料表包含資料列參考時更新資料行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6d2d3509b51d083290339514083a541ef9a86b64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030654"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>在其他資料表包含資料列參考時更新資料行

某些提供者可以偵測哪些資料行中資料列變更，但許多提供者不能。 如此一來，更新資料行可能會導致發生錯誤時您嘗試更新資料列的參考。 若要解決此問題，請建立包含您想要變更的資料行的個別存取子。 傳遞至該存取子數目`SetData`。  
  
## <a name="see-also"></a>另請參閱  

[使用存取子](../../data/oledb/using-accessors.md)