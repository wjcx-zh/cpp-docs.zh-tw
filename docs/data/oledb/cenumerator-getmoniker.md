---
title: CEnumerator::GetMoniker | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
dev_langs:
- C++
helpviewer_keywords:
- GetMoniker method
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6049dfc14bb6ebe46f173ec07e536102acdebb3c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cenumeratorgetmoniker"></a>CEnumerator::GetMoniker
剖析顯示名稱，以擷取元件可以轉換成 moniker 的字串。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  


HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *ppMoniker*  
 [out]Moniker 所剖析的顯示名稱 ([cenumeratoraccessor:: M_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) 的目前資料列。  
  
 *lpszDisplayName*  
 [in]要剖析的顯示名稱。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CEnumerator 類別](../../data/oledb/cenumerator-class.md)