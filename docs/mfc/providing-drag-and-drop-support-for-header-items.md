---
title: 提供為標題項目拖放支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50cd19d4828269d0591afd0b46768e9917b96906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349340"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>為標題項目提供拖放支援
若要針對標題項目提供拖放功能支援，請指定 `HDS_DRAGDROP` 樣式。 為標題項目提供的拖放功能支援可讓使用者重新排列標題控制項的標題項目。 如果置放標題項目，預設行為會提供拖曳之標題項目的半透明拖曳影像，以及新位置的視覺指標。  
  
 因為一般拖放功能，您可以延伸預設拖放行為由處理**HDN_BEGINDRAG**和**HDN_ENDDRAG**通知。 您也可以藉由覆寫自訂拖曳影像的外觀[cheaderctrl:: Createdragimage](../mfc/reference/cheaderctrl-class.md#createdragimage)成員函式。  
  
> [!NOTE]
>  如果您在清單控制項為內嵌的標題控制項提供拖放支援，請參閱 < 延伸樣式 」 一節[變更清單控制項樣式](../mfc/changing-list-control-styles.md)主題。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

