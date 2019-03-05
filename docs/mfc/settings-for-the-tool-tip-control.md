---
title: 工具提示控制項的設定
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 5cc72401da95e63520b544865ea509a8ad219bda
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271927"
---
# <a name="settings-for-the-tool-tip-control"></a>工具提示控制項的設定

您可以將工具提示控制項 ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) 設為作用中或非作用中。 當您將它設為作用中時，當游標位於工具上時，會出現工具提示控制項。 當您將它設為非作用中時，即使游標位於工具上，也不會出現工具提示控制項。 呼叫 [Activate](../mfc/reference/ctooltipctrl-class.md#activate) 啟用或停用工具提示控制項。

您可以設定要顯示工具提示，當游標位於工具，工具提示控制項的主控視窗在作用中，使用 TTS_ALWAYSTIP 樣式在作用中的工具提示。 如果不使用這個樣式，當工具的主控視窗在作用中時會出現工具提示控制項，但非作用中時則不會出現。

大部分的應用程式包含對應至功能表命令之工具的工具列。 針對這類工具，工具提示控制項若能顯示與對應功能表項目相同的文字會很方便。 系統會自動去除 & 符號加速器字元，從所有字串傳遞至工具提示控制項，除非控制項有 TTS_NOPREFIX 樣式。

## <a name="see-also"></a>另請參閱

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
