---
title: MFC 和 ATL 共用的類別
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491451"
---
# <a name="classes-shared-by-mfc-and-atl"></a>MFC 和 ATL 共用的類別

下表列出 MFC 與 ATL 之間共用的類別。

|類別|描述|標頭檔|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|提供用來管理與檔案相關聯之日期和時間值的方法。|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|提供方法來管理與檔案相關聯的相對日期和時間值。|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|表示具有固定字元緩衝區的字串物件。|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增強的點陣圖支援, 包括以 JPEG、GIF、BMP 和可移植網狀圖形 (PNG) 格式載入和儲存影像的能力。|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|封裝 OLE automation 中使用的日期資料類型。|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|表示相對時間 (時間範圍)。|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|類似于 Windows[點](/windows/win32/api/windef/ns-windef-point)結構的類別, 其中也包含操作`CPoint`和`POINT`結構的成員函式。|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|類似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)結構的類別, 其中也包含用來操作`CRect`物件和 Windows `RECT`結構的成員函式。|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|`CSimpleStringT`代表物件。|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|類似于 Windows[大小](/windows/win32/api/windef/ns-windef-size)結構的類別, 它會實作為相對座標或位置。|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|針對`GetBuffer` `ReleaseBuffer`現有的`CStringT`物件, 提供和呼叫的自動資源清除。|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|表示字串物件的資料。|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|`CStringT`代表物件。|cstringt .h (MFC 相依) 和 atlstr.h .h (MFC 獨立)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|代表絕對時間和日期。|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|一段時間, 在內部儲存為時間範圍內的秒數。|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|表示`CStringT`記憶體管理員的介面。|atlsimpstr.h|

## <a name="see-also"></a>另請參閱

[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
