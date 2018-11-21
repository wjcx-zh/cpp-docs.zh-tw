---
title: 進度控制項的樣式
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 5d33e9306c1d70bb58ad628297360bc6e34e6ce2
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174950"
---
# <a name="styles-for-the-progress-control"></a>進度控制項的樣式

當您一開始建立進度控制項 ([cprogressctrl:: Create](../mfc/reference/cprogressctrl-class.md#create))，使用*cheaderctrl:: Create*參數來指定進度控制項的所需的視窗樣式。 下列清單詳細說明了適用的視窗樣式。 控制項會忽略除了此清單所列以外的所有視窗樣式。 您必須將控制項建立為子視窗，通常會以對話方塊為父代。

|視窗樣式|作用|
|------------------|------------|
|WS_BORDER|在視窗周圍建立框線。|
|WS_CHILD|建立子視窗 (應永遠為 `CProgressCtrl` 所使用)。|
|WS_CLIPCHILDREN|在父視窗內繪圖時，應排除子視窗佔用的區域。 當您建立父視窗時使用。|
|WS_CLIPSIBLINGS|裁剪相對於彼此的子視窗。|
|WS_DISABLED|建立一個一開始即停用的視窗。|
|WS_VISIBLE|建立一個一開始即可見的視窗。|
|WS_TABSTOP|指定控制項在使用者按下 TAB 鍵並移至它時可以接收焦點。|

此外，您可以指定兩種樣式只套用至進度控制項，PBS_VERTICAL 和 PBS_SMOOTH。

使用 PBS_VERTICAL 垂直，而非水平放置控制項。 您可以使用 PBS_SMOOTH 完全填滿控制項，而不是顯示小型分隔的方格，以累加方式填入控制項。

沒有 PBS_SMOOTH 樣式：

![標準進度列樣式](../mfc/media/vc4ruw1.gif "標準進度列樣式")

PBS_SMOOTH 和 PBS_VERTICAL 樣式：

![進度列的樣式、 平滑和垂直](../mfc/media/vc4ruw2.gif "進度列的樣式、 平滑和垂直")

如需詳細資訊，請參閱 <<c0> [ 的視窗樣式](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc)中*MFC 參考 》*。

## <a name="see-also"></a>另請參閱

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)

