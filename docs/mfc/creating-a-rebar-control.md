---
title: 建立 Rebar 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1deb33adc104775cf9b76daf75d4ee08b6475f0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342303"
---
# <a name="creating-a-rebar-control"></a>建立 Rebar 控制項
[CReBarCtrl](../mfc/reference/crebarctrl-class.md)應該建立物件，在父物件顯示之前。 如此可以將繪製發生問題的可能性降到最低。  
  
 例如，Rebar 控制項 (用於框架視窗物件) 通常當做工具列控制項的父視窗使用。 因此，Rebar 控制項的父代為框架視窗物件。 由於框架視窗物件是父代，因此父代的 `OnCreate` 成員函式是建立 Rebar 控制項的絕佳位置。  
  
 若要使用 `CReBarCtrl` 物件，您通常會執行下列步驟：  
  
### <a name="to-use-a-crebarctrl-object"></a>使用 CReBarCtrl 物件  
  
1.  建構[CReBarCtrl](../mfc/reference/crebarctrl-class.md)物件。  
  
2.  呼叫[建立](../mfc/reference/crebarctrl-class.md#create)建立 Windows rebar 通用控制項並將其附加至`CReBarCtrl`物件，指定所需的任何樣式。  
  
3.  載入點陣圖，以呼叫[cbitmap:: Loadbitmap](../mfc/reference/cbitmap-class.md#loadbitmap)，以當做 rebar 控制項物件的背景。  
  
4.  建立並初始化 Rebar 控制項中將包含的任何子視窗物件 (工具列、對話方塊控制項等)。  
  
5.  初始化**REBARBANDINFO**即將要插入的寬線的必要資訊的結構。  
  
6.  呼叫[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)插入現有的子視窗 (例如`m_wndReToolBar`) 插入新的 rebar 控制項。 如需有關如何將群組列插入現有 rebar 控制項的詳細資訊，請參閱[Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

