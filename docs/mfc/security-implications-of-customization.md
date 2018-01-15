---
title: "自訂的安全性影響 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b408b4595e95016323d2b43f1ed51fc6e2e6d244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="security-implications-of-customization"></a>自訂的安全性影響
本主題將討論 MFC 中潛在的安全性弱點。  
  
## <a name="potential-security-weakness"></a>潛在的安全性弱點  
 MFC 可讓使用者自訂應用程式使用者介面的外觀，例如按鈕和圖示的外觀。 MFC 也支援使用者定義的工具，可讓使用者執行殼層命令。 安全性弱點出現的原因是因為應用程式的自訂設定都儲存在登錄的使用者設定檔中。 可以存取登錄的人都可以編輯這些設定並變更應用程式的外觀或行為。 例如，電腦的系統管理員可能會促使使用者的應用程式執行任意程式，來模擬使用者 (即使是從網路共用)。  
  
## <a name="workarounds"></a>替代解決辦法  
 我們建議以下列三種方式之一來封閉登錄中的漏洞：  
  
-   將儲存在其中的資料加密  
  
-   將資料改為儲存在安全的檔案而不是在登錄中。  
  
     若要完成其中一種將前兩個，衍生自[CSettingsStore 類別](../mfc/reference/csettingsstore-class.md)並覆寫其方法來實作加密或外部登錄的存放裝置。  
  
-   您也可以停用應用程式的自訂。  
  
## <a name="see-also"></a>請參閱  
 [MFC 自訂](../mfc/customization-for-mfc.md)

