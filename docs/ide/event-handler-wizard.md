---
title: "事件處理常式精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords: Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ccb80add8a98b9251a7ccbb5c85bf98b610a22e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="event-handler-wizard"></a>事件處理常式精靈
此精靈會將對話方塊控制項的事件處理常式加入至您選擇的類別。 如果您加入事件處理常式從[屬性 視窗](/visualstudio/ide/reference/properties-window)，您可以將它只會加入可實作對話方塊中的類別。 請參閱[加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)如需詳細資訊。  
  
 **命令名稱**  
 識別選取的控制項，為其加入事件處理常式。 無法使用此方塊。  
  
 **訊息類型**  
 顯示所選控制項的目前可能的訊息處理常式的清單。  
  
 **函式的處理常式名稱**  
 顯示新增至處理事件的函式的名稱。 根據預設，名稱根據訊息類型和命令，前面加上的 「 開啟 」。 例如，按鈕呼叫`IDC_BUTTON1`，訊息類型`BN_CLICKED`顯示函式的處理常式名稱`OnBnClickedButton1`。  
  
 **類別清單**  
 顯示可用的類別，您可以新增事件處理常式。 [選取] 對話方塊的類別會以紅色顯示。  
  
 **處理常式描述**  
 為選取的項目提供描述**訊息類型**方塊。 無法使用此方塊。  
  
 **新增和編輯**  
 將訊息處理常式加入至選取的類別或物件，並讓您加入控制項告知處理常式程式碼，然後開啟新的函式的文字編輯器。  
  
 **編輯程式碼**  
 開啟文字編輯器來選取現有的函式，以便您可以新增或編輯控制項告知處理常式程式碼。  
  
## <a name="see-also"></a>請參閱  
 [加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)