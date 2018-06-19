---
title: 'Crowset:: Close |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b56cd48a61ceab242081c1323a267b21be661ad4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096726"
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
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)