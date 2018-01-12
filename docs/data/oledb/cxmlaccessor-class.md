---
title: "CXMLAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs: C++
helpviewer_keywords: CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 96620f287522168cd7b6b78d43163e8c4bb64217
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 類別
可讓您存取資料來源做為字串資料，當您在不知道資料存放區的結構描述 （基礎結構）。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA 類別](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 類別](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)