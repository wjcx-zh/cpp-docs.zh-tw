---
title: CRowsetImpl::GetColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3cbcc7c25983680f32f1d5982188a853d8215358
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
擷取特定的用戶端要求的資料行資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>參數  
 `pv`  
 [in]使用者的指標`CRowsetImpl`衍生的類別。  
  
 `pcCols`  
 [in]指標 （輸出） 的數字傳回的資料行。  
  
## <a name="return-value"></a>傳回值  
 靜態的指標**ATLCOLUMNINFO**結構。  
  
## <a name="remarks"></a>備註  
 這個方法是進階的覆寫。  
  
 呼叫這個方法是由數個基底實作類別，以擷取特定的用戶端要求的資料行資訊。 通常，這個方法會由呼叫`IColumnsInfoImpl`。 如果您覆寫這個方法，您必須將放在方法的版本您`CRowsetImpl`-衍生的類別。 因為此方法可能會放置於非樣板化的類別，您必須變更`pv`適當`CRowsetImpl`-衍生的類別。  
  
 下列範例會示範**GetColumnInfo 的**使用量。 在此範例中， **CMyRowset**是`CRowsetImpl`-衍生的類別。 若要覆寫`GetColumnInfo`這個類別的所有執行個體，將下列方法在**CMyRowset**類別定義：  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)