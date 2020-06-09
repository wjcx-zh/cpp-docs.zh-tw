---
title: 影像清單中的影像資訊
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c12198c769585763095d22b73d11f7af3c9d6fc0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624503"
---
# <a name="image-information-in-image-lists"></a>影像清單中的影像資訊

[CImageList](reference/cimagelist-class.md)包含一些函式，可從影像清單中取出資訊。 [GetImageInfo](reference/cimagelist-class.md#getimageinfo)成員函式會 `IMAGEINFO` 以單一影像的相關資訊來填滿結構，包括影像和遮罩點陣圖的控制碼、色彩平面的數目和每圖元的位數，以及影像點陣圖內影像的周框。 您可以使用此項資訊直接操作影像的點陣圖。

[GetImageCount](reference/cimagelist-class.md#getimagecount)成員函式會抓取影像清單中的影像數目。

您可以使用[ExtractIcon](reference/cimagelist-class.md#extracticon)成員函式，根據影像清單中的影像和遮罩來建立圖示。 函式會傳回新圖示的控制代碼。

## <a name="see-also"></a>另請參閱

[使用 CImageList](using-cimagelist.md)<br/>
[控制項](controls-mfc.md)
