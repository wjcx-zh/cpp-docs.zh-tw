---
title: CBookmark::operator = | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
dev_langs:
- C++
helpviewer_keywords:
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: 23805af4-aedd-47ad-bef4-21d902463797
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c2a5b77d84167a5d051224934447ce8d377b0cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cbookmarkoperator-"></a>CBookmark::operator =
指派 `CBookmark` 物件給另一個。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CBookmark& operator =(const CBookmark& bookmark) throw();  
```  
  
## <a name="remarks"></a>備註  
 這個運算子只有在需要**CBookmark\<0 >**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)