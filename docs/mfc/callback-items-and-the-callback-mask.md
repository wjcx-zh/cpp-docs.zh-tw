---
title: 回呼項目和回呼遮罩
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 1c46f6edb44e4898c0245209ca837cd0eb716304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624964"
---
# <a name="callback-items-and-the-callback-mask"></a>回呼項目和回呼遮罩

對於其各個項目中，清單檢視控制項通常會儲存標籤文字、項目圖示的影像清單索引，和一組用於項目狀態的位元旗標。 如果您的應用程式已經儲存某個項目的一些資訊，將個別項目定義為回呼項目會很有用。

您可以為結構的和成員指定適當的值，以將專案定義為回呼專案 `pszText` `iImage` `LVITEM` （請參閱[CListCtrl：： GetItem](reference/clistctrl-class.md#getitem)）。 如果應用程式維護專案或子項的文字，請指定成員的**LPSTR_TEXTCALLBACK**值 `pszText` 。 如果應用程式持續追蹤專案的圖示，請指定成員的**I_IMAGECALLBACK**值 `iImage` 。

除了定義回呼項目之外，您也可以修改控制項的回呼遮罩。 這個遮罩是一組指定儲存目前資料之應用程式 (而不是控制項) 項目狀態的位元旗標。 回呼遮罩適用於所有控制項的項目，與套用至特定項目的回呼項目指定不同。 回呼遮罩預設為零，表示控制項正在追蹤所有項目的狀態。 若要變更此預設行為，請將遮罩初始化為下列值的任何組合：

- **LVIS_CUT**專案會標示為剪下和貼上作業。

- **LVIS_DROPHILITED**專案會反白顯示為拖放目標。

- **LVIS_FOCUSED**專案具有焦點。

- **LVIS_SELECTED**已選取專案。

- **LVIS_OVERLAYMASK**應用程式會儲存每個專案之目前重迭影像的影像清單索引。

- **LVIS_STATEIMAGEMASK**應用程式會儲存每個專案之目前狀態影像的影像清單索引。

如需有關抓取和設定此遮罩的進一步資訊，請參閱[CListCtrl：： GetCallbackMask](reference/clistctrl-class.md#getcallbackmask)和[CListCtrl：： SetCallbackMask](reference/clistctrl-class.md#setcallbackmask)。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
