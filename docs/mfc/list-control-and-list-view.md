---
title: 清單控制項和清單檢視
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621433"
---
# <a name="list-control-and-list-view"></a>清單控制項和清單檢視

為了方便起見，MFC 以兩種方式封裝清單控制項。 您可以下列方式來使用清單控制項：

- 直接，藉由在對話方塊類別中內嵌[CListCtrl](reference/clistctrl-class.md)物件。

- 藉由使用 [類別[CListView](reference/clistview-class.md)] 間接進行。

`CListView`可讓您輕鬆地將清單控制項與 MFC 檔/視圖架構整合，將控制項封裝起來就像[CEditView](reference/ceditview-class.md)封裝編輯控制項一樣：控制項會填滿 MFC 視圖的整個介面區。 （此視圖*是*控制項，轉換為 `CListView` ）。

`CListView`物件繼承自[CCtrlView](reference/cctrlview-class.md)及其基類，並加入成員函式以取得基礎清單控制項。 使用檢視成員來運用檢視。 使用[GetListCtrl](reference/clistview-class.md#getlistctrl)成員函式來取得清單控制項的成員函式的存取權。 使用這些成員：

- 在清單中加入、刪除或操作「項目」。

- 設定或取得清單控制項屬性。

若要取得以 `CListCtrl` 為基礎的 `CListView` 的參考，請從清單檢視類別呼叫 `GetListCtrl`：

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

本主題說明兩種使用清單控制項的方式。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
