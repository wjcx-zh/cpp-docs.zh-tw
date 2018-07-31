---
title: 資料列集物件介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e8a1a5f5256087a8869426489fe01250b16fc598
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340507"
---
# <a name="rowset-object-interfaces"></a>資料列集物件介面
下表顯示由 OLE DB 定義的資料列集物件的必要和選用的介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)|強制|[是]|  
|[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)|強制|[是]|  
|[IConvertType](https://msdn.microsoft.com/library/ms715926.aspx)|強制|[是]|  
|[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)|強制|[是]|  
|[IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx)|強制|[是]|  
|[IChapteredRowset](https://msdn.microsoft.com/library/ms718180.aspx)|Optional|否|  
|[IColumnsInfo2](https://msdn.microsoft.com/library/ms712953.aspx)|Optional|否|  
|[IColumnsRowset](https://msdn.microsoft.com/library/ms722657.aspx)|Optional|否|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|是 （透過 ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/library/ms709832.aspx)|Optional|否|  
|[IGetRow](https://msdn.microsoft.com/library/ms718047.aspx)|Optional|否|  
|[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)|Optional|[是]|  
|[IRowsetChapterMember](https://msdn.microsoft.com/library/ms725430.aspx)|Optional|否|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/library/ms709700.aspx)|Optional|否|  
|[IRowsetFind](https://msdn.microsoft.com/library/ms724221.aspx)|Optional|否|  
|[IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)|選擇性 （但必要層級 0 提供者）|[是]|  
|[IRowsetIndex](https://msdn.microsoft.com/library/ms719604.aspx)|Optional|否|  
|[IRowsetLocate](https://msdn.microsoft.com/library/ms721190.aspx)|Optional|[是]|  
|[IRowsetRefresh](https://msdn.microsoft.com/library/ms714892.aspx)|Optional|否|  
|[IRowsetScroll](https://msdn.microsoft.com/library/ms712984.aspx)|Optional|否|  
|[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)|Optional|[是]|  
|[IRowsetView](https://msdn.microsoft.com/library/ms709755.aspx)|Optional|否|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Optional|[是]|  
|[IRowsetBookmark](https://msdn.microsoft.com/library/ms714246.aspx)|Optional|否|  
  
 精靈產生的資料列集物件會實作`IAccessor`， `IRowset`，和`IRowsetInfo`透過繼承。 `IAccessorImpl`繫結這兩個輸出資料行。 `IRowset`介面會處理擷取資料列和資料。 `IRowsetInfo`介面會處理資料列集屬性。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)