---
title: "何時需要呼叫 AtlAxWinTerm？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinTerm
dev_langs: C++
helpviewer_keywords: AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdba5255560f220a80a016f17e574721b12f486d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>何時需要呼叫 AtlAxWinTerm？
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)取消註冊**"AtlAxWin80"**視窗類別。 您應該呼叫此函式 （如果您不需要再建立主應用程式視窗） 終結所有現有的主控件 windows。 如果您未呼叫此函式，視窗類別會自動取消註冊處理序終止時。  
  
## <a name="see-also"></a>另請參閱  
 何時需要呼叫 AtlAxWinInit  
[控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

