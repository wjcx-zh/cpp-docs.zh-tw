---
title: CXMLAccessor 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs:
- C++
helpviewer_keywords:
- CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 916e9dbe4e142192e4e716f57f97d5bd6865c709
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 類別
可讓您存取資料來源做為字串資料，當您在不知道資料存放區的結構描述 （基礎結構）。  
  
## <a name="syntax"></a>語法

```cpp
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|擷取的資料行資訊。|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|資料列來擷取資料表的整個內容。|  
  
## <a name="remarks"></a>備註  
 不過，`CXMLAccessor`不同於`CDynamicStringAccessorW`，它會將轉換從資料存放區做為 XML 格式 （標記） 的資料存取的所有資料。 這是特別適用於輸出至 XML 感知的 Web 網頁。 XML 標記名稱會儘可能密集地符合資料存放區的資料行名稱。  
  
 使用`CDynamicAccessor`方法，取得資料行資訊。 您可以使用此資料行資訊在執行階段動態建立存取子。  
  
 資料行資訊會儲存在緩衝區中建立和管理由這個類別。 取得資料行資訊使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)或取得資料行資料所使用的資料列[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭檔**：atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)