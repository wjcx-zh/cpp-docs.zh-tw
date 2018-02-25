---
title: "ICommandImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec1c9bb3a430b30350ca3940fc7c90e6758d7c40
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimpl-class"></a>ICommandImpl 類別
提供實作[ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`ICommandImpl`。  
  
 `CommandBase`  
 命令介面。 預設值為 `ICommand`。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|取消目前執行的命令。|  
|[取消](../../data/oledb/icommandimpl-cancel.md)|取消目前執行的命令。|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|建立資料列集物件。|  
|[Execute](../../data/oledb/icommandimpl-execute.md)|執行命令。|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|傳回建立命令的工作階段的介面指標。|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|建構函式。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|指出是否要取消命令。|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|指出命令是否要取消時執行。|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|指出目前是否正在執行的命令。|  
  
## <a name="remarks"></a>備註  
 Command 物件上的強制介面。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)