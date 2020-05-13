---
title: 簡單資料類型類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365404"
---
# <a name="simple-data-type-classes"></a>簡單資料類型類別

下列類別會封裝繪圖座標、字元字串以及時間和日期資訊，以便於使用 C++ 語法。 這些物件廣泛當做類別庫中 Windows 類別的成員函式的參數使用。 因為`CPoint``CSize``CRect`, 和 對應於 Windows SDK 中的**POINT、SIZE**和**RECT**結構,因此無論使用這些 C 語言**SIZE**結構,都可以使用這些 C++類的物件。 類別可透過其成員函式提供實用的介面。 `CStringT` 提供非常彈性的動態字元字串。 `CTime``COleDateTime`,`CTimeSpan``COleTimeSpan`表示 時間和日期值。 有關這些類的詳細資訊,請參閱文章[「日期和時間](../atl-mfc-shared/date-and-time.md)」。。

以""`COle`開頭的類別是 OLE 提供的資料類型的封裝。 不論是否使用其他 OLE 功能，這些資料類型都可用於 Windows 程式。

[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
保存字元字串。

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
保存絕對時間和日期值。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自動化型**態 DATE**的包裝器 。 表示日期和時間值。

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
保存相對時間和日期值。

[COleDatetimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
保存 `COleDateTime` 的相對值，例如兩個 `COleDateTime` 值之間的差值。

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保存 (x, y) 座標組。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保存距離、相對位置或配對的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保存矩形區域的座標。

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
提供 Windows 影像清單的功能。 影像清單是搭配清單控制項和樹狀目錄控制項使用。 也可以用來儲存和封存一組大小相同的點陣圖。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE 自動化型**態 VARIANT**的包裝器 。 **VARIANT**中的數據可以以多種格式存儲。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE 自動化類型**貨幣**的包裝器,一種定點算術類型,在小數點之前有 15 位元數位,後為 4 位。

> [!NOTE]
> `CRect``CSize`,`CPoint`並且可用於 ATL 或 MFC 應用程式。 此外,`CStringT`還提供與 MFC 無關`CString`的類。 有關共用實用程式類的詳細資訊,請參閱[共享類](../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
