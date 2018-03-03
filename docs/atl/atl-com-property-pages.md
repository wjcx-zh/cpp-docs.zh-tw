---
title: "ATL COM 屬性頁 |Microsoft 文件"
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
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1c31aeaba25f4eadad5225dd2f5607cf7053c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-com-property-pages"></a>ATL COM 屬性頁
COM 屬性頁來設定屬性提供使用者介面 （或呼叫的方法） 的一或多個 COM 物件。 屬性頁大量使用 ActiveX 控制項提供豐富的使用者介面可讓要在設計階段設定控制項屬性。  
  
 屬性頁可讓您為 COM 物件實作[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)或[IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996)介面。 這些介面提供允許頁面與相關聯的方法`site`（代表網頁的容器的 COM 物件） 和一些*物件*會呼叫其方法，以回應變更 （COM 物件使用者所做的屬性頁）。 屬性頁容器會負責告訴頁面時顯示或隱藏其使用者介面，以及何時將變更套用到使用者所做的基礎物件的屬性頁面介面上呼叫方法。  
  
 每個屬性頁可完全建立獨立的物件，您可以設定其屬性。 所有屬性頁需求是，了解特定介面 （或一組介面），並提供使用者介面，該介面上呼叫方法。  
  
 如需詳細資訊，請參閱[屬性工作表和屬性頁](http://msdn.microsoft.com/library/windows/desktop/ms686577)中[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [指定屬性頁](../atl/specifying-property-pages.md)  
 列出指定控制項的屬性頁的步驟，並顯示範例類別。  
  
 [實作屬性頁](../atl/implementing-property-pages.md)  
 列出實作屬性頁中，包括要覆寫方法的步驟。 逐步解說 ATLPages 範例程式為基礎的完整範例。  
  
## <a name="related-sections"></a>相關章節  
 [ATLPages 範例](../visual-cpp-samples.md)  
 ATLPages 範例中，實作屬性的頁面使用的範例摘要`IPropertyPageImpl`。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。  
  
## <a name="see-also"></a>請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)

