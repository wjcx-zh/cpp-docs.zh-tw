---
title: 新增事件精靈 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f83ff02329a373e6ba65315cf33f7cb21145eb48
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402664"
---
# <a name="add-event-wizard"></a>加入事件精靈

此精靈會將事件新增至 MFC ActiveX 控制項專案。 您可以指定自己的事件、自訂一般內建的事件，或從內建事件的清單中選取。

- **事件名稱**

   設定 Automation 用戶端用來從類別要求事件的名稱。 輸入名稱或從清單中選取。

- **事件類型**

   指示要新增的事件類型。 只有當您從 [事件名稱] 清單選取時可用。

   |選項|描述|
   |------------|-----------------|
   |**內建**|指定將會為這個類別實作內建的事件，例如按一下按鈕。 內建事件定義在 Microsoft Foundation Class (MFC) 程式庫中。|
   |**自訂**|指定您要提供自己的事件實作。|

- **內部名稱**

   設定傳送事件的成員函式名稱。 僅適用於自訂事件。 名稱是根據 [事件名稱]。 如果您想要提供不同於 [事件名稱] 的名稱，您可以變更內部名稱。

- **參數類型**

   設定 [參數名稱] 的類型。 從清單中選取類型。

- **參數名稱**

   設定要透過事件傳遞的參數名稱。 鍵入名稱之後，您必須按一下 [新增]，將它新增至參數清單。

   按一下 [新增] 之後，參數名稱會出現在 [參數清單] 中。

   > [!NOTE]
   > 如果您提供參數名稱，然後按一下 [完成] 再按一下 [新增]，則參數不會新增至事件。 您必須尋找方法，並手動插入參數。 **參數清單**

- **[新增]**

   將您在 [參數名稱] 中指定的參數及其類型，新增至 [參數清單]。 您必須按一下 [新增]，才能將參數新增至清單。

- **移除**

   將您在 [參數清單] 中選取的參數從清單移除。

- **參數清單**

   顯示目前針對方法新增的所有參數及類型。 新增參數時，精靈會更新 [參數清單] 以顯示每個參數及其類型。

## <a name="see-also"></a>請參閱

[新增事件](../ide/adding-an-event-visual-cpp.md)