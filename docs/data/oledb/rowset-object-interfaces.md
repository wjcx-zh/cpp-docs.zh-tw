---
title: 資料列集物件介面
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311687"
---
# <a name="rowset-object-interfaces"></a>資料列集物件介面

下表顯示 OLE DB 針對資料列集物件所定義的必要和選擇性介面。

|介面|必要項？|由 OLE DB 範本來執行？|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|強制|是|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|強制|是|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|強制|是|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|強制|是|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|強制|是|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|選擇性|否|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|選擇性|否|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|選擇性|否|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|選擇性|是（透過 ATL）|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|選擇性|否|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|選擇性|否|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|選擇性|是|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|選擇性|否|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|選擇性|否|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|選擇性|否|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|選擇性（但層級0提供者需要）|是|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|選擇性|否|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|選擇性|是|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|選擇性|否|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|選擇性|否|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|選擇性|是|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|選擇性|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|選擇性|是|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|選擇性|否|

Wizard 產生的資料列集物件`IAccessor`會`IRowset`透過繼承`IRowsetInfo`來執行、和。 `IAccessorImpl`會系結兩個輸出資料行。 `IRowset`介面會處理提取資料列和資料。 `IRowsetInfo`介面會處理資料列集屬性。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
