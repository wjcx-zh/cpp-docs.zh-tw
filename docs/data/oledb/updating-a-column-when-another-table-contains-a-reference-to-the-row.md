---
title: "另一個資料表包含資料列參考時更新資料行 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5b4d4c041e1a6ad0f40107ef2bfb71293c05e5d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>在其他資料表包含資料列參考時更新資料行
某些提供者可以偵測資料列變更，哪些資料行，但許多提供者不能。 如此一來，更新的資料行可能會導致發生錯誤時嘗試更新資料列的參考。 若要解決此問題，請建立包含您想要變更的資料行的個別存取子。 傳遞至該存取子數目`SetData`。  
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)