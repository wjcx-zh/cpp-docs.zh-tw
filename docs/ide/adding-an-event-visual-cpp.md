---
title: 新增事件
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: 1d5a8f5666dd04e00f8a438fdbf00320c37e14f4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693421"
---
# <a name="add-an-event"></a>新增事件

從 [類別檢視] 中，您可以使用[新增事件精靈](#add-event-wizard)，只將事件新增至 [MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)專案中的控制項類別。 如果您想要將事件新增至另一種專案，請使用[屬性視窗](/visualstudio/ide/reference/properties-window)中的 [事件] 按鈕。

**將事件新增至 MFC ActiveX 控制項專案：**

1. 在 [類別檢視] 中，展開專案節點，顯示專案中的類別。

1. 以滑鼠右鍵按一下專案的控制項類別。

1. 在捷徑功能表上，選擇 [新增]，然後選擇 [新增事件] 顯示 [新增事件精靈]。

1. 在適當的精靈方塊中提供事件資訊。

1. 選取 [完成]，將事件新增至專案。

## <a name="in-this-section"></a>本節內容

- [新增事件精靈](#add-event-wizard)

## <a name="add-event-wizard"></a>新增事件精靈

此精靈會將事件新增至 MFC ActiveX 控制項專案。 您可以指定自己的事件、自訂一般內建事件，或從內建事件的清單中選取。

- **事件名稱**

   設定 Automation 用戶端用來從類別要求事件的名稱。 輸入名稱或從清單中選取。

- **事件類型**

   指示要新增的事件類型。 只有當您從 [事件名稱] 清單中選取時才可用。

   |選項|描述|
   |------------|-----------------|
   |**內建**|指定將會為這個類別實作內建的事件，例如按一下按鈕。 內建事件定義在 Microsoft Foundation Class (MFC) 程式庫中。|
   |**自訂**|指定您要使用自己的事件實作。|

- **內部名稱**

   設定傳送事件的成員函式名稱。 僅適用於自訂事件。 名稱是根據 [事件名稱]。 如果您想要提供不同於 [事件名稱] 的名稱，您可以變更內部名稱。

- **參數類型**

   設定 [參數名稱] 的類型。 從清單中選取類型。

- **參數名稱**

   設定要透過事件傳遞的參數名稱。 鍵入名稱之後，您必須選取 [新增]，將它新增至參數清單。

   選取 [新增] 後，參數名稱會出現在 [參數清單] 中。

   > [!NOTE]
   > 如果您提供參數名稱，然後選取 [完成] 再選取 [新增]，則參數不會新增至事件。 您必須尋找方法，並手動插入參數。

- **[新增]**

   將您在 [參數名稱] 中指定的參數及其類型，新增至 [參數清單]。 選取 [新增]，將參數新增至清單中。

- **移除**

   將您在 [參數清單] 中選取的參數從清單移除。

- **參數清單**

   顯示目前針對方法新增的所有參數及類型。 新增參數時，精靈會更新 [參數清單] 以顯示每個參數及其類型。
