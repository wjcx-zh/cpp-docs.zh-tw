---
title: 影像清單中的影像資訊
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: 7b83b7e5f7de6f8ccca95d732f71a5d73a97e943
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363514"
---
# <a name="image-information-in-image-lists"></a>影像清單中的影像資訊

[CImageList](../mfc/reference/cimagelist-class.md)包含數個函式，從影像清單擷取資訊。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成員函式會填滿`IMAGEINFO`單一映像，包括影像和遮罩點陣圖、 色彩平面和每像素的位元的數目和週框矩形的控制代碼的相關資訊的結構影像點陣圖內影像。 您可以使用此項資訊直接操作影像的點陣圖。

[GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成員函式擷取的映像清單中的映像數目。

您可以建立圖示的影像和遮罩影像清單中的使用根據[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成員函式。 函式會傳回新圖示的控制代碼。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
