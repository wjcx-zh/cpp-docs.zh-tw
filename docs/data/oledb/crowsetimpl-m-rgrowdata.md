---
title: CRowsetImpl::m_rgRowData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
dev_langs:
- C++
helpviewer_keywords:
- m_rgRowData
ms.assetid: e4e75ca7-12e8-4a0b-94e8-e395c21385b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecb6cb3b8bb840cb75a91f0e5674e4bab5c0dc67
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetimplmrgrowdata"></a>CRowsetImpl::m_rgRowData
根據預設，`CAtlArray`上的使用者資料錄的樣板引數，templatizes `CRowsetImpl`。  
  
## <a name="syntax"></a>語法  
  
```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;  
  
```  
  
## <a name="remarks"></a>備註  
 **ArrayType**為範本參數`CRowsetImpl`。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)   
 [CRowsetImpl::m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)