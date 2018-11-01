---
title: 樹狀目錄控制項影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 2b680ece131df434b65f02501f78f0cdb6507f08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551758"
---
# <a name="tree-control-image-lists"></a>樹狀目錄控制項影像清單

樹狀結構控制項中的每個項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以有一組與其相關聯的點陣圖影像。 映像會出現在左邊的項目標籤。 選取的項目，和其他顯示項目若未選取時，會顯示一個映像。 例如，項目可能會顯示開啟的資料夾時選取它並關閉的資料夾時未選取。

若要使用的項目映像，您必須建立影像清單建構[CImageList](../mfc/reference/cimagelist-class.md)物件並使用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)函式來建立相關聯的映像清單。 然後將所需的點陣圖新增至清單中，並使用與樹狀目錄控制項相關聯的清單[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成員函式。 根據預設，所有的項目會顯示第一個映像，在映像清單中選取及未選取狀態。 您可以藉由指定的選取和未選取映像的索引，將項目加入至樹狀目錄控制項使用時變更特定項目的預設行為[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成員函式。 您可以變更索引之後使用 新增項目[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成員函式。

樹狀目錄控制項影像清單也可以包含專為重疊，項目影像的覆疊影像。 非零值的樹狀目錄控制項目狀態的位元 8 到 11 指定的其中一個基礎覆疊影像的索引 （0 表示無覆疊影像）。 使用 4 位元，以一為基的索引，因為覆疊影像必須是在前 15 的映像，映像清單中。 如需有關樹狀目錄控制項目狀態的詳細資訊，請參閱[樹狀目錄控制項項目狀態概觀](../mfc/tree-control-item-states-overview.md)稍早在本主題。

如果指定了狀態映像清單，樹狀目錄控制項就會保留到狀態影像的每個項目圖示左邊的空間。 應用程式可以使用狀態的影像，例如核取或清除核取方塊，以指出應用程式定義的項目狀態。 非零的值，以位元 12 至 15 指定以一為基的索引狀態影像 （0 表示無狀態影像）。

藉由指定**I_IMAGECALLBACK**值而不是影像的索引，您可以延遲指定所選取或未選取的映像，直到重新繪製項目。 **I_IMAGECALLBACK**會指示樹狀目錄控制項來查詢索引的應用程式傳送[TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo)通知訊息。

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成員函式會擷取樹狀目錄控制項影像清單的控制代碼。 此函式是很有用，如果您需要將更多映像新增至清單。 如需有關影像清單的詳細資訊，請參閱[使用 CImageList](../mfc/using-cimagelist.md)， [CImageList](../mfc/reference/cimagelist-class.md)中*MFC 參考 》*，並[影像清單](https://msdn.microsoft.com/library/windows/desktop/bb761389)中Windows SDK。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

