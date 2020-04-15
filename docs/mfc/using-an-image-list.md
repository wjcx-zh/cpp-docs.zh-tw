---
title: 使用影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366566"
---
# <a name="using-an-image-list"></a>使用影像清單

影像清單的典型用法遵循以下模式:

- 建構[CImageList](../mfc/reference/cimagelist-class.md)物件並呼叫其[Create](../mfc/reference/cimagelist-class.md#create)函數的重載之一以創建影像清單`CImageList`並將其附加到 物件。

- 如果在創建圖像清單時未添加圖像,請透過呼叫[「添加](../mfc/reference/cimagelist-class.md#add)」或[「讀取](../mfc/reference/cimagelist-class.md#read)」成員」功能將圖像添加到影像清單中。

- 通過調用該控制件的相應成員函數將圖像清單與控制項關聯,或使用圖像清單的[「繪製](../mfc/reference/cimagelist-class.md#draw)」成員函數自行從圖像清單中繪製圖像。

- 可能允許使用者使用圖像清單的內置支援拖動來拖動圖像。

> [!NOTE]
> 如果影像清單是**使用新**運算符創建的,則必須在使用`CImageList`該 物件時銷毀該物件。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
