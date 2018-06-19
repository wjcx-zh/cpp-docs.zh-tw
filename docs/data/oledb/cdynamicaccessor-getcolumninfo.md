---
title: 'Cdynamicaccessor:: Getcolumninfo |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c9fe862f08fc9ecfa280dcbb55f48e14427d6ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091890"
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
傳回所需的大部分取用者的資料行中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `pRowset`  
 [in]指標[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)介面。  
  
 *pColumns*  
 [out]記憶體中的資料列集; 傳回的資料行數目的指標如果有的話，此數值包含書籤資料行。  
  
 *ppColumnInfo*  
 [out]這是要傳回的陣列中的記憶體指標**DBCOLUMNINFO**結構。 請參閱中的"DBCOLUMNINFO 結構" [icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  
  
 `ppStringsBuffer`  
 [out]要在其中儲存的所有字串值會傳回指標記憶體的指標 (使用名稱內*columnid*或*pwszName*) 單一配置區塊內。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 請參閱[icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程式設計人員參考*如需資料類型資訊**DBORDINAL**， **DBCOLUMNINFO**，和**OLECHAR**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)