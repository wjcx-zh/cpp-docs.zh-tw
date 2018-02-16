---
title: "CDynamicParameterAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5eaea3f682fc31c825849ba4d3b5b48166f085ef
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor 類別

類似於[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)取得參數資訊，藉由呼叫設定，但[ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)介面。

## <a name="syntax"></a>語法

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|建構函式。|
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|從緩衝區擷取參數資料。|
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|擷取存取子中的參數數目。|
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|判斷指定的參數為輸入或輸出參數。|
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|擷取儲存在緩衝區中的指定參數的長度。|
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|擷取指定的參數名稱。|
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|擷取儲存在緩衝區中的指定參數的狀態。|
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|擷取儲存在緩衝區中的指定參數的字串資料。|
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|擷取指定參數的資料類型。|
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|設定使用參數資料的緩衝區。|
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|設定儲存在緩衝區中的指定參數的長度。|
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|設定儲存在緩衝區中的指定參數的狀態。|
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|設定儲存在緩衝區中的指定參數的字串資料。|

## <a name="remarks"></a>備註

提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。

參數資訊會儲存在這個類別建立和管理的緩衝區中。 使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)從緩衝區取得參數資料。

如需示範如何使用這個類別來執行 SQL Server 預存程序並取得輸出參數值的範例，請參閱[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)範例程式碼中的[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)GitHub 上的儲存機制。

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor 類別](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)  
