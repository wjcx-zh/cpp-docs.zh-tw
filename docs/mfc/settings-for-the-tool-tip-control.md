---
title: "工具提示控制項的設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "工具提示 [C++], 啟用"
  - "CToolTipCtrl 類別, 設定"
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 工具提示控制項的設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將工具提示控制項 \([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)\) 設為作用中或非作用中。 當您將它設為作用中時，當游標位於工具上時，會出現工具提示控制項。 當您將它設為非作用中時，即使游標位於工具上，也不會出現工具提示控制項。 呼叫 [Activate](../Topic/CToolTipCtrl::Activate.md) 啟用或停用工具提示控制項。  
  
 您可以使用 **TTS\_ALWAYSTIP** 樣式，設定作用中的工具提示，則無論工具提示控制項的主控視窗是否在作用中，當游標位於工具上時都會顯示工具提示。 如果不使用這個樣式，當工具的主控視窗在作用中時會出現工具提示控制項，但非作用中時則不會出現。  
  
 大部分的應用程式包含對應至功能表命令之工具的工具列。 針對這類工具，工具提示控制項若能顯示與對應功能表項目相同的文字會很方便。 系統會自動從傳遞至工具提示控制項的所有字串移除 & 符號加速器字元，除非控制項有 **TTS\_NOPREFIX** 樣式。  
  
## 請參閱  
 [Using CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)