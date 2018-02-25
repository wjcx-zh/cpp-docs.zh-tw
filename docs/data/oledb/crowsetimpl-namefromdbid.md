---
title: CRowsetImpl::NameFromDBID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 623eeca73ceaf29e0cecbe80b2a4a8b447adefdc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
擷取從字串**DBID**並將它複製到`bstr`傳入。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>參數  
 *pDBID*  
 [in]指標**DBID**要從中擷取字串。  
  
 `bstr`  
 [in]A [CComBSTR](../../atl/reference/ccombstr-class.md)參考的副本放入**DBID**字串。  
  
 `bIndex`  
 [in]**true**如果索引**DBID**;**false**如果資料表**DBID**。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 取決於是否**DBID**是資料表或索引 (以表示`bIndex`)，此方法將會回到**DB_E_NOINDEX**或**DB_E_NOTABLE**。  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫`CRowsetImpl`實作[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)