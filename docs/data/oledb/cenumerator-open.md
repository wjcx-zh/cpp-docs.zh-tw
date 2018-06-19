---
title: 'Cenumerator:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 04e6884b27f45ee86085c1b820376ed087ae68c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096921"
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
列舉值，繫結 moniker，如果其中一個指定，則擷取的資料列集列舉值，藉由呼叫[isourcesrowset:: Getsourcesrowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx)。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  


HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  


HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `pMoniker`  
 [in]Moniker，以便查看的列舉值指標。  
  
 *pClsid*  
 [in]指標**CLSID**的列舉值。  
  
 `enumerator`  
 [in]列舉值的參考。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CEnumerator 類別](../../data/oledb/cenumerator-class.md)