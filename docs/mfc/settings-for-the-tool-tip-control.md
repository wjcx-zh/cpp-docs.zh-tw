---
title: 設定工具提示控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b61fb9450e6206c8f96102b5feeec6fbf3bead3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="settings-for-the-tool-tip-control"></a>工具提示控制項的設定
您可以將工具提示控制項 ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) 設為作用中或非作用中。 當您將它設為作用中時，當游標位於工具上時，會出現工具提示控制項。 當您將它設為非作用中時，即使游標位於工具上，也不會出現工具提示控制項。 呼叫 [Activate](../mfc/reference/ctooltipctrl-class.md#activate) 啟用或停用工具提示控制項。  
  
 您可以使用 **TTS_ALWAYSTIP** 樣式，設定作用中的工具提示，則無論工具提示控制項的主控視窗是否在作用中，當游標位於工具上時都會顯示工具提示。 如果不使用這個樣式，當工具的主控視窗在作用中時會出現工具提示控制項，但非作用中時則不會出現。  
  
 大部分的應用程式包含對應至功能表命令之工具的工具列。 針對這類工具，工具提示控制項若能顯示與對應功能表項目相同的文字會很方便。 系統會自動移除從傳遞至工具提示控制項時，所有字串的 & 符號加速器字元，除非控制項有**TTS_NOPREFIX**樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)

