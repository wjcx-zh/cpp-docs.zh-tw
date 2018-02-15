---
title: CRowset::Close | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset::Close
- ATL.CRowset.Close
- CRowset<TAccessor>::Close
- CRowset<TAccessor>.Close
- ATL.CRowset<TAccessor>.Close
- ATL::CRowset::Close
- ATL::CRowset<TAccessor>::Close
- CRowset.Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 966d779e-e148-4dc0-bbba-7cfb9fa6a16b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 48056f59482c0fc9750aed07a2aa394178fc5b18
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetclose"></a>CRowset::Close
釋放資料列和目前[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
void Close() throw();  
  
```  
  
## <a name="remarks"></a>備註  
 這個方法會釋出目前在資料列集中的所有資料列。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)