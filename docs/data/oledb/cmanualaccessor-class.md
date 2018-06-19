---
title: CManualAccessor 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b8efc46971b1aa72f8c5e572aa540bfed250d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098169"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 類別
代表設計供進階使用存取子類型。  
  
## <a name="syntax"></a>語法

```cpp
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|將繫結項目加入至輸出資料行。|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|將參數項目加入至參數存取子。|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|資料行繫結結構配置記憶體並初始化的資料行的資料成員。|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|參數繫結結構配置記憶體並初始化參數資料成員。|  
  
## <a name="remarks"></a>備註  
 使用`CManualAccessor`，您可以指定參數，輸出資料行繫結的執行階段函式呼叫。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)