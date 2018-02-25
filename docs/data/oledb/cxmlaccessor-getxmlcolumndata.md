---
title: CXMLAccessor::GetXMLColumnData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLColumnData method
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 52b968dac5efbc4ceb41499a55c6be12d51dd0da
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cxmlaccessorgetxmlcolumndata"></a>CXMLAccessor::GetXMLColumnData
依資料行擷取為 XML 格式的字串資料，資料表的資料行型別資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `strOutput`  
 [out]包含要擷取的資料行型別資訊的字串緩衝區的參考。 比對資料存放區的資料行名稱的 XML 標記名稱以格式化字串。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 下圖顯示在 XML 中格式化的資料行型別資訊的方式。 `type` 指定資料行的資料類型。 請注意，資料類型基礎 OLE DB 資料類型，不屬於所存取的資料庫。  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)