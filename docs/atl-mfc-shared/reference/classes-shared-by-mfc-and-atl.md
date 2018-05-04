---
title: 類別由 MFC 和 ATL 共用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea651297503210a78f3ee189c57e37bcc3e99c6a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="classes-shared-by-mfc-and-atl"></a>類別由 MFC 和 ATL 共用。
下表列出 MFC 和 ATL 之間共用的類別  
  
|類別|描述|標頭檔|  
|-----------|-----------------|-----------------|  
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|提供管理與檔案相關聯的日期和時間值的方法。|atltime.h|  
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|提供管理相對日期和時間值與檔案相關聯的方法。|atltime.h|  
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|表示具有固定的字元緩衝區的字串物件。|cstringt.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增強的點陣圖支援，包括載入和儲存 JPEG、 GIF、 BMP、 及可攜式網路圖形 (PNG) 格式的映像的能力。|atlimage.h|  
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|封裝**日期**OLE automation 中使用的資料類型。|atlcomtime.h|  
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|代表相對時間、 時間範圍。|atlcomtime.h|  
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|類別類似於 Windows[點](../../mfc/reference/point-structure1.md)結構，其中也包含成員函式來管理`CPoint`和**點**結構。|atltypes.h|  
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|類別類似於 Windows [RECT](../../mfc/reference/rect-structure1.md)結構，其中也包含成員函式來管理`CRect`物件和 Windows`RECT`結構。|atltypes.h|  
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|代表`CSimpleStringT`物件。|atlsimpstr.h|  
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|類別類似於 Windows 大小結構，它會實作相對座標或位置。|atltypes.h|  
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|提供的自動資源清除`GetBuffer`和`ReleaseBuffer`呼叫上的現有`CStringT`物件。|atlsimpstr.h|  
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|表示字串物件中的資料。|atlsimpstr.h|  
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|代表`CStringT`物件。|cstringt.h （MFC 相依） atlstr.h （MFC 獨立）|  
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|代表絕對時間和日期。|atltime.h|  
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|在內部儲存為時間範圍中的秒數的時間量。|atltime.h|  
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|代表介面，以`CStringT`記憶體管理員。|atlsimpstr.h|  
  
## <a name="see-also"></a>另請參閱  
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)


