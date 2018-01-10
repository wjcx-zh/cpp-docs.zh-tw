---
title: "Cenumerator:: Open |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a5c35b3806e04f20417c7053248d1a098456403
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
列舉值，繫結 moniker，如果其中一個指定，則擷取的資料列集列舉值，藉由呼叫[isourcesrowset:: Getsourcesrowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT Open(   
   LPMONIKER pMoniker    
) throw( );  
HRESULT Open(   
   const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR    
) throw( );  
HRESULT Open(   
   const CEnumerator& enumerator    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `pMoniker`  
 [in]Moniker，以便查看的列舉值指標。  
  
 *Createtable*  
 [in]指標**CLSID**的列舉值。  
  
 `enumerator`  
 [in]列舉值的參考。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CEnumerator 類別](../../data/oledb/cenumerator-class.md)