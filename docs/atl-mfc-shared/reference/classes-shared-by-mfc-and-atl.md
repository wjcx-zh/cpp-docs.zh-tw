---
title: 由 MFC 和 ATL 共用類別
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 6e63664020508252a61682c46439af85033cf068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583868"
---
# <a name="classes-shared-by-mfc-and-atl"></a>由 MFC 和 ATL 共用類別

下表列出 MFC 和 ATL 之間共用的類別

|類別|描述|標頭檔|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|提供方法來管理與檔案相關聯的日期和時間值。|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|提供用於管理相對的日期和時間值與檔案相關聯的方法。|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|代表固定的字元緩衝區的字串物件。|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增強的點陣圖支援，包括載入和儲存 JPEG、 GIF、 BMP、 和可攜式網路圖形 (PNG) 格式的映像的能力。|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|封裝 OLE automation 中使用的日期資料類型。|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|代表相對的時間，時間範圍。|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|類似於 Windows 的類別[點](../../mfc/reference/point-structure.md)結構，其中也包含成員函式來操作`CPoint`和`POINT`結構。|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|類似於 Windows 的類別[RECT](../../mfc/reference/rect-structure.md)結構，其中也包含成員函式來操作`CRect`物件和 Windows`RECT`結構。|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|代表`CSimpleStringT`物件。|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|類似於 Windows SIZE 結構，於實作相對座標或位置的類別。|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|提供的自動資源清除作業`GetBuffer`並`ReleaseBuffer`呼叫現有`CStringT`物件。|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|表示字串物件的資料。|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|代表`CStringT`物件。|cstringt.h （MFC 相依） 和 （MFC 獨立）|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|表示絕對的時間和日期。|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|一段時間，這會在內部儲存為時間範圍中的秒數。|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|表示介面`CStringT`記憶體管理員。|atlsimpstr.h|

## <a name="see-also"></a>另請參閱

[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

