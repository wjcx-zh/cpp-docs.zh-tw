---
title: CXMLAccessor::GetXMLRowData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e356be7a5ab7c125dc92a822384a3e6b02b8f8e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
擷取為 XML 格式的字串資料的資料表的整個內容依資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,   
   bool bAppend = false) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `strOutput`  
 [out]包含要擷取的資料表資料之緩衝區的參考。 資料會格式化為字串資料，以符合資料存放區的資料行名稱的 XML 標記名稱。  
  
 *bAppend*  
 [in]布林值，指定是否要將字串附加至輸出資料的結尾。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 下圖顯示在 XML 中格式化的資料列資料的方式。 `DATA` 下面代表資料列資料。 使用 move 方法移至所需的資料列。  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CXMLAccessor 類別](../../data/oledb/cxmlaccessor-class.md)