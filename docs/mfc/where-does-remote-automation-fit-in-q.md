---
title: "Remote Automation 適用於什麼情況？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation, DCOM
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad6eef0bbaad7860e7f4310ce283efe18c668eb
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="where-does-remote-automation-fit-in"></a>Remote Automation 適用於什麼情況？
DCOM 發行於 1996 年，並且只適用於 32 位元和 64 位元平台。 Microsoft 的 Visual Basic 小組一直將 Visual Basic 視為使用 Automation 來允許其元件進行通訊。 缺少分散式版本嚴重限制了這些功能在企業環境中的使用，因此開發 Visual Basic 4.0 企業版的小組決定調查其為 OLE 和 COM 的 Automation 組件所建立的一組遠端元件。 顯然主要目標是為了確保結果會相容，並且可以在 DCOM 可用時由其取代。 他們接著繼續實作 16 位元和 32 位元 Windows 平台的 Remote Automation (RA)。  
  
 Remote Automation 未繫結至任何特定語言，但是直到 Visual C++ 4.2 企業版發行前僅隨附於 Visual Basic 4.0。 請注意，Remote Automation 是整個屬於 DCOM 的範圍內。 如果您有機會在應用程式中使用 DCOM 而非 Remote Automation，則應如此做。 儘管如此，有些案例還是 Remote Automation 比較適當：  
  
-   只要您有 16 位元用戶端。  
  
-   如果您的組織沒有使用啟用 DCOM 版本的 Windows NT 或 Windows 95。  
  
-   如果您將使用 Remote Automation 的現有應用程式套件升級為在一個或多個 Visual Basic 元件位置使用 C++ 元件。  
  
 在建立為使用 Remote Automation 的程式和建立為在 DCOM 上使用 Automation 的程式之間，必須沒有差別，而設定公用程式可使得在 Remote Automation 和 DCOM 之間的作業切換變得非常簡單。 其結果是，一旦基礎結構就緒之後，將應用程式從 Remote Automation 升級至 DCOM 就不是那麼困難了。  
  
## <a name="see-also"></a>請參閱  
 [Remote Automation 提供什麼功能](what-does-remote-automation-provide-q.md)   
 [DCOM 的歷史](../mfc/history-of-dcom.md)
