---
title: "初始化對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2af05011e8f2af2993edf3ea2f82716137b17857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-the-dialog-box"></a>初始化對話方塊
對話方塊之後方塊和其控制項的所有已建立，但對話方塊之前 （一種類型） 的方塊會出現在畫面上，對話方塊物件的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)呼叫成員函式。 對於強制回應對話方塊，這會在 `DoModal` 期間發生。 對於非強制回應對話方塊，`OnInitDialog`時，會呼叫**建立**呼叫。 通常會覆寫 `OnInitDialog` 以初始化對話方塊的控制項，例如設定編輯方塊的初始文字。 您必須從您的 `OnInitDialog` 覆寫呼叫基底類別 `CDialog` 的 `OnInitDialog` 成員函式。  
  
 如果您想要設定對話方塊的背景色彩 （以及程式的應用程式中所有其他對話方塊），請參閱[設定對話方塊的背景色彩](../mfc/setting-the-dialog-boxs-background-color.md)。  
  
## <a name="see-also"></a>請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

