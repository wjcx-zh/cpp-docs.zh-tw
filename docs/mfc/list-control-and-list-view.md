---
title: 清單控制項和清單檢視 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9925bd7188faa97ab5aa32dc2830dc6498726381
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436750"
---
# <a name="list-control-and-list-view"></a>清單控制項和清單檢視

為了方便起見，MFC 以兩種方式封裝清單控制項。 您可以下列方式來使用清單控制項：

- 直接透過內嵌[CListCtrl](../mfc/reference/clistctrl-class.md)對話方塊類別中的物件。

- 使用類別來間接[CListView](../mfc/reference/clistview-class.md)。

`CListView` 可讓您輕鬆地整合使用 MFC 的文件/檢視架構，封裝控制項的清單控制項十分類似[CEditView](../mfc/reference/ceditview-class.md)封裝編輯控制項： 控制項會填滿 MFC 檢視的整個介面區。 (檢視*已*控制項，轉換成`CListView`。)

A`CListView`物件繼承自[CCtrlView](../mfc/reference/cctrlview-class.md)和其基底類別，並將成員函式來擷取基礎清單控制項。 使用檢視成員來運用檢視。 使用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)成員函式來取得清單控制項的成員函式的存取權。 使用這些成員：

- 在清單中加入、刪除或操作「項目」。

- 設定或取得清單控制項屬性。

若要取得以 `CListCtrl` 為基礎的 `CListView` 的參考，請從清單檢視類別呼叫 `GetListCtrl`：

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

本主題說明兩種使用清單控制項的方式。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

