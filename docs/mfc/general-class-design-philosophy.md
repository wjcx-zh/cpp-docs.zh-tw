---
title: "一般類別設計原理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c174b06b27e78ca61d2608b8e04205068ac436e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="general-class-design-philosophy"></a>一般類別設計原理
Microsoft Windows 的設計是 c + + 語言變得熱門之前。 由於數千個應用程式使用 C 語言的 Windows 應用程式開發介面 (API)，該介面會維護可預見的未來。 因此必須之上程序的 C 語言應用程式開發介面建置任何 c + + Windows 介面。 這可確保 c + + 應用程式能夠與 C 應用程式並存。  
  
 Microsoft Foundation 類別庫為物件導向的介面，以符合下列設計目標的 Windows:  
  
-   投入時間來寫入 Windows 應用程式明顯降低。  
  
-   相當於 C 語言應用程式開發介面的執行速度。  
  
-   最小的程式碼大小的額外負荷。  
  
-   直接呼叫任何 Windows C 函式的能力。  
  
-   轉換現有 c + + 的 C 應用程式更容易。  
  
-   能夠利用現有的基底的 C 語言 Windows 程式設計經驗。  
  
-   更容易使用比 c 與 c + + 的 Windows api  
  
-   容易使用但功能強大的抽象概念的複雜功能，例如 ActiveX 控制項、 資料庫支援、 列印、 工具列和狀態列。  
  
-   有效地使用 c + + 語言功能的 c + + 的 Windows API，則為 true。  
  
 如需 MFC 程式庫設計的詳細資訊，請參閱：  
  
-   [應用程式架構](../mfc/application-framework.md)  
  
-   [與 C 語言 API 的關聯性](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

