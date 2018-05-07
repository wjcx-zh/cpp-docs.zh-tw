---
title: IRowsetNotifyImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 860b735863acbcac869a4a297984084946aaf028
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 類別
實作並註冊[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)上取用者 （也稱為 「 接收 」），好讓它可以處理通知。  
  
## <a name="syntax"></a>語法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|通知的取用者的資料行值的任何變更。|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|告知消費者的資料列的第一個變更或是任何會影響整個資料列的變更。|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|通知任何變更會影響整個資料列集取用的者。|  
  
## <a name="remarks"></a>備註  
 請參閱[接收通知](../../data/oledb/receiving-notifications.md)有關上取用者實作連接點介面。  
  
 `IRowsetNotifyImpl` 提供的虛擬實作`IRowsetNotify`，空函式與`IRowsetNotify`方法[OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)， [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)，和[OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx). 如果您繼承自這個類別實作時`IRowsetNotify`介面，您可以實作您所需要的方法。 您也需要自行提供空其他方法的實作。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)