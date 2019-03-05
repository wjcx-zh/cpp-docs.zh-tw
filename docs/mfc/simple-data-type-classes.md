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
ms.openlocfilehash: 4e415805301d7d12bd418a3b55509a7732851492
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298473"
---
# <a name="simple-data-type-classes"></a>簡單資料類型類別

下列類別會封裝繪圖座標、字元字串以及時間和日期資訊，以便於使用 C++ 語法。 這些物件廣泛當做類別庫中 Windows 類別的成員函式的參數使用。 因為`CPoint`， `CSize`，並`CRect`對應至**點**，**大小**，並**RECT**結構，分別在 Windows SDK 中，只要您可以使用這些 C-語言結構，您可以使用這些 c + + 類別的物件。 類別可透過其成員函式提供實用的介面。 `CStringT` 提供非常彈性的動態字元字串。 `CTime``COleDateTime`， `CTimeSpan`，和`COleTimeSpan`代表日期和時間值。 如需有關這些類別的詳細資訊，請參閱文章[日期和時間](../atl-mfc-shared/date-and-time.md)。

開頭的類別 「`COle`"是 OLE 所提供的資料類型的封裝。 不論是否使用其他 OLE 功能，這些資料類型都可用於 Windows 程式。

[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
保存字元字串。

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
保存絕對時間和日期值。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE automation 類型包裝函式**日期**。 表示日期和時間值。

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
保存相對時間和日期值。

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
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
OLE automation 類型包裝函式**VARIANT**。 中的資料**VARIANT**s 可儲存許多格式。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE automation 類型包裝函式**貨幣**，定點算術類型，則 15 位數，小數點之前與之後有 4 位數。

> [!NOTE]
>  `CRect``CSize`，和`CPoint`可在 ATL 或 MFC 應用程式中使用。 颾魤 ㄛ`CStringT`提供的 MFC 無關`CString`-和類別一樣。 如需有關共用公用程式類別的詳細資訊，請參閱[共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
