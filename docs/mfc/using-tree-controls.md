---
title: 使用樹狀目錄控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9cb5c8892583adac01ca883034b8c0af18595c9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954591"
---
# <a name="using-tree-controls"></a>使用樹狀目錄控制項
樹狀目錄控制項的一般使用方式 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 遵循下列模式：  
  
-   建立控制項。 如果控制項在對話方塊範本中指定，或如果您使用`CTreeView`，建立對話方塊或檢視時，會自動建立。 如果您想要建立做為一些其他視窗的子視窗的樹狀結構控制項中，使用[建立](../mfc/reference/ctreectrl-class.md#create)成員函式。  
  
-   如果您要使用影像樹狀目錄控制項，來設定影像清單呼叫[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)。 您也可以藉由呼叫來變更縮排[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)。 若要這樣做的好時機處於[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) （適用於在對話方塊中的控制項） 或[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) （適用於檢視）。  
  
-   將資料放入控制項，藉由呼叫`CTreeCtrl`的[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)函式，針對每個資料項目執行一次。 `InsertItem` 控制代碼傳回至項目，以便日後參考，例如當加入子項目。 初始化資料的好時機處於`OnInitDialog`（適用於在對話方塊中的控制項） 或`OnInitialUpdate`（適用於檢視）。  
  
-   當使用者與控制項互動時，它會傳送各種通知訊息。 您可以指定函式，以處理每個您想要在控制項視窗的訊息對應中加入 ON_NOTIFY_REFLECT 巨集或將 ON_NOTIFY 巨集加入至父視窗的訊息對應處理的訊息。 請參閱[樹狀目錄控制項通知訊息](../mfc/tree-control-notification-messages.md)本主題稍後的一份可能的通知。  
  
-   呼叫各種 Set 成員函式以設定控制項的值。 您可以進行的變更包括設定縮排和變更文字、 影像或項目相關聯的資料。  
  
-   您可以使用各種 Get 函式來檢查控制項的內容。 您也可以周遊樹狀目錄控制項的功能，可讓您擷取父系、 子系，以及指定之項目的同層級的控制代碼的內容。 您甚至可以排序特定節點的子系。  
  
-   當您完成控制項時，請確定已正確地終結。 如果樹狀目錄控制項位於對話方塊中，或者它是一個檢視，它和`CTreeCtrl`物件將會自動終結。 否則，您必須確保控制項和 `CTreeCtrl` 物件都已正確地終結。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

