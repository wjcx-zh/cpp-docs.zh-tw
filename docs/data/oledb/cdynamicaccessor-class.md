---
title: CDynamicAccessor 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4006afa9ebdfcf95a01103d1fd97643a6b749f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 類別
讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。  
  
## <a name="syntax"></a>語法

```cpp
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|覆寫預設存取子時，請將繫結項目加入至輸出資料行中。|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|執行個體化並初始化`CDynamicAccessor`物件。|  
|[關閉](../../data/oledb/cdynamicaccessor-close.md)|所有資料行解除繫結，釋放配置的記憶體，並釋放[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)類別中的介面指標。|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|擷取目前的資料列的書籤。|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|擷取 BLOB 處理目前的資料列的值。|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|擷取最大 BLOB 大小 （位元組）。|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|擷取資料列集中的資料行的數目。|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|擷取的資料行的特性。|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|擷取資料行中繼資料。|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|擷取指定之資料行名稱。|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|擷取指定之資料行的資料類型。|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|擷取的資料行，以位元組為單位的最大可能長度。|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|擷取指定的資料行名稱的資料行索引。|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|擷取指定之資料行的狀態。|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|從緩衝區中擷取資料。|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|設定 BLOB 處理目前的資料列的值。|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|設定最大 BLOB 大小 （位元組）。|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|設定資料行的長度，以位元組為單位。|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|設定指定之資料行的狀態。|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|儲存至緩衝區的資料。|  
  
## <a name="remarks"></a>備註  
 使用`CDynamicAccessor`方法，取得資料行資訊，例如資料行名稱、 資料行計數、 資料類型，等等。 然後，您會使用此資料行資訊在執行階段動態建立存取子。  
  
 資料行資訊會儲存在緩衝區中，建立和管理由這個類別。 取得資料緩衝區使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)。  
  
 討論和使用動態存取子類別的範例，請參閱[使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。  
  
## <a name="requirements"></a>需求  
 **標頭檔**：atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)