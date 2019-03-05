---
title: 使用樹狀目錄控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 9cff48018d728ef9578be38c0d94300011265fa1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258316"
---
# <a name="using-tree-controls"></a>使用樹狀目錄控制項

典型的使用方式的樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 會遵循下列模式：

- 建立控制項。 如果在對話方塊範本中指定的控制項，或如果您使用`CTreeView`，建立對話方塊或檢視時，會自動建立。 如果您想要建立做為一些其他視窗的子視窗的樹狀結構控制項中，使用[建立](../mfc/reference/ctreectrl-class.md#create)成員函式。

- 如果您想要使用映像樹狀目錄控制項，藉由呼叫中設定的映像清單[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)。 您也可以藉由呼叫來變更縮排[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)。 若要這樣做的好時機處於[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) （適用於在對話方塊中的控制項） 或[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) （適用於檢視）。

- 藉由呼叫時，將資料放入控制項`CTreeCtrl`的[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)函式，針對每個資料項目執行一次。 `InsertItem` 傳回控制代碼以便日後參考，例如當項目加入子項目。 初始化資料的好時機處於`OnInitDialog`（適用於在對話方塊中的控制項） 或`OnInitialUpdate`（適用於檢視）。

- 當使用者與控制項互動時，它會傳送各種通知訊息。 您可以指定函式以處理每個您想要處理控制項視窗的訊息對應中新增 ON_NOTIFY_REFLECT 巨集，或將 ON_NOTIFY 巨集加入至父視窗的訊息對應的訊息。 請參閱[樹狀目錄控制項通知訊息](../mfc/tree-control-notification-messages.md)本主題稍後如需可能的通知的清單。

- 呼叫各種 Set 成員函式以設定控制項的值。 您可以進行變更，包括設定縮排和變更的文字、 影像或項目相關聯的資料。

- 您可以使用各種 Get 函式來檢查控制項的內容。 您也可以周遊樹狀目錄控制項的功能，可讓您擷取父代、 子系，和指定的項目 的同層級的控制代碼的內容。 您甚至可以排序特定節點的子系。

- 當您完成控制項時，請確定已正確地終結。 如果樹狀結構控制項在對話方塊中，或者它是一個檢視，它和`CTreeCtrl`物件將會自動終結。 否則，您必須確保控制項和 `CTreeCtrl` 物件都已正確地終結。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
