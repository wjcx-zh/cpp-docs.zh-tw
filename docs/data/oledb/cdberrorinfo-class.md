---
title: CDBErrorInfo 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59222e30fe4a0ee7914c4a4d4e8dfa0d6d3a260b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 類別
支援使用 OLE DB 的 OLE DB 錯誤處理[IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
class CDBErrorInfo  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|傳回包含錯誤記錄中的所有錯誤資訊。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|呼叫[IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx)來傳回指定的錯誤相關的基本資訊。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|呼叫[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)來傳回自訂錯誤物件介面的指標。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|呼叫[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)傳回**IErrorInfo**介面指標，指向指定的記錄。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|呼叫[IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)傳回錯誤參數。|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|取得指定之物件的錯誤記錄。|  
  
## <a name="remarks"></a>備註  
 這個介面會傳回給使用者的一或多個錯誤記錄。 呼叫[cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)第一個，以取得錯誤記錄的計數。 然後呼叫其中一個存取函式，例如[cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)，擷取每一筆記錄資訊時發生錯誤。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)