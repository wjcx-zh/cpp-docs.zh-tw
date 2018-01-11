---
title: "管理目前檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1510b005f452174acfe8ad65ae3f66cf8aafaa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="managing-the-current-view"></a>管理目前的檢視
在框架視窗的預設實作中，會持續記錄目前作用中的檢視。 如果框架視窗包含一個以上的檢視，例如在分割視窗中，目前的檢視就是最近使用中的檢視。 現用檢視表是獨立於 Windows 中的使用中視窗或目前的輸入焦點之外。  
  
 當現用檢視變更時，架構會通知目前的檢視藉由呼叫其[OnActivateView](../mfc/reference/cview-class.md#onactivateview)成員函式。 您可以檢查 `OnActivateView`'s `bActivate` 參數來判斷檢視目前是否已啟用或停用。 根據預設，`OnActivateView` 會在啟用時將焦點設定在目前的檢視。 當檢視停用或重新啟用時，您可以覆寫 `OnActivateView` 以執行任何特殊處理。 例如，您可能想要提供特殊視覺提示以區別現用檢視和其他非現用檢視。  
  
 框架視窗會將其目前 （現用） 的檢視，命令中所述[命令路由](../mfc/command-routing.md)，做為標準命令路由的一部分。  
  
## <a name="see-also"></a>請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)

