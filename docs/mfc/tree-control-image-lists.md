---
title: 樹狀目錄控制項影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 8f9e323244657ea6a7cc132deab6deedfcd1a167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513368"
---
# <a name="tree-control-image-lists"></a>樹狀目錄控制項影像清單

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的每個專案都可以有一對與它相關聯的點陣圖影像。 影像會出現在專案標籤的左側。 當選取專案時, 會顯示一個影像, 另一個則會在未選取專案時顯示。 例如, 專案可能會在選取時顯示開啟的資料夾, 而當未選取時, 則會顯示 [已關閉] 資料夾。

若要使用專案影像, 您必須藉由建立[CImageList](../mfc/reference/cimagelist-class.md)物件並使用[CImageList:: create](../mfc/reference/cimagelist-class.md#create)函式來建立相關聯的影像清單, 以建立影像清單。 然後, 將所需的點陣圖新增至清單, 並使用[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成員函式將清單與樹狀目錄控制項產生關聯。 根據預設, 所有專案都會在影像清單中顯示所選和 nonselected 狀態的第一個影像。 當您使用[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成員函式將專案新增至樹狀目錄控制項時, 可以藉由指定所選取和 nonselected 影像的索引, 來變更特定專案的預設行為。 您可以使用[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成員函式, 在新增專案之後變更索引。

樹狀目錄控制項的影像清單也可以包含重迭影像, 其設計是要在專案影像上重迭。 樹狀目錄控制項的狀態中, 位8到11的非零值會指定重迭影像的以一為基礎的索引 (0 表示沒有重迭影像)。 由於使用了4位的以一為基礎的索引, 因此重迭影像必須是影像清單中的前15個影像。 如需樹狀目錄控制項專案狀態的詳細資訊, 請參閱本主題稍早的[樹狀目錄控制項專案狀態總覽](../mfc/tree-control-item-states-overview.md)。

如果指定了狀態影像清單, 樹狀目錄控制項會在狀態影像的每個專案圖示左邊保留空間。 應用程式可以使用狀態影像 (如 [已核取] 和 [已清除] 核取方塊) 來表示應用程式定義的專案狀態。 位12到15的非零值會指定狀態影像的以一為基礎的索引 (0 表示沒有狀態影像)。

藉由指定**I_IMAGECALLBACK**值而不是影像的索引, 您可以延遲指定選取或 nonselected 的影像, 直到專案即將重新繪製為止。 **I_IMAGECALLBACK**會透過傳送[TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo)通知訊息, 引導樹狀目錄控制項查詢索引的應用程式。

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成員函式會抓取樹狀目錄控制項之影像清單的控制碼。 如果您需要將更多影像加入清單中, 此函式會很有用。 如需影像清單的詳細資訊, 請參閱 <<c0>使用 CImageList、 *MFC 參考*中的[CImageList](../mfc/reference/cimagelist-class.md)和 Windows SDK 中的[影像清單](/windows/win32/controls/image-lists)。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
