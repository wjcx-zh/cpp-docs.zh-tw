---
title: "主動式文件內含項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16c0311c3eedc13cbc47214b44fc8810dee3eecd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="active-document-containment"></a>主動式文件內含項目
主動式文件內含項目是一種技術，提供要使用的文件，而不是強迫您建立及用於每個文件類型的多個應用程式框架中的單一框架。 它會與基本 OLE 技術的 OLE 適用於只有單一內容可以為作用中的複合文件中內嵌的物件。 使用中文件內含項目，您可以啟用整個文件 （也就是整個應用程式，包括相關聯的功能表、 工具列和等等） 單一框架的內容中。  
  
 主動式文件內含項目技術原先是針對實作 Office Binder 的 Microsoft Office 開發。 不過，技術有足夠的彈性，以支援 Office Binder 以外的主動式文件容器，並可支援文件伺服程式 Office 和 Office 相容的應用程式以外。  
  
 裝載主動式文件的應用程式會呼叫[主動式文件容器](../mfc/active-document-containers.md)。 這類容器的範例是 Microsoft Office Binder 或 Microsoft Internet Explorer。  
  
 主動式文件內含項目會實作為一組延伸模組 ole 文件、 OLE 複合文件技術。 擴充功能都是允許的內嵌就地物件來代表整份文件，而不是單一的內嵌內容的其他介面。 如同 OLE 文件，主動式文件內含項目會使用提供的顯示空間主動式文件，並提供使用者介面與管理功能的作用中的文件本身的伺服器的容器。  
  
 [主動式文件伺服](../mfc/active-document-servers.md)是支援應用程式 （例如 Word、 Excel 或 PowerPoint） 的一或多個主動式文件類別，其中每個物件本身支援允許要在中啟用物件的延伸模組介面適合的容器。  
  
 [使用中文件](../mfc/active-documents.md)（提供從使用中文件伺服器，例如 Word 或 Excel） 是基本上是的大規模、 傳統文件會內嵌為另一個使用中的文件容器中的物件。 不同於內嵌物件，主動式文件擁有完整控制權其頁面中，以及完整的介面，將應用程式 （具有所有其基礎的命令與工具） 可加以編輯使用者。  
  
 主動式文件加以了解，以利從標準 OLE 內嵌物件。 OLE 慣例，內嵌的物件是內擁有它，文件的頁面會顯示可管理的 OLE 容器文件。 容器會儲存與文件的其餘部分的內嵌的物件的資料。 不過，內嵌的物件會受到限制，因為它們並不控制它們出現的頁面。  
  
 主動式文件容器應用程式的使用者可以建立主動式文件 （稱為 Office Binder 中的章節） 使用他們最愛的應用程式 （假設這些應用程式都支援主動式文件），但使用者可以管理與產生的專案單一實體，可以唯一地命名、 儲存，列印，依此類推。 同樣地，在網際網路瀏覽器的使用者可以將整個網路，以及本機檔案系統，視為單一文件儲存體實體瀏覽該存放裝置從單一位置中的文件的能力。  
  
## <a name="sample-programs"></a>範例程式  
  
-   [MFCBIND](../visual-cpp-samples.md)範例說明實作主動式文件容器應用程式。  
  
## <a name="see-also"></a>請參閱  
 [MFC COM](../mfc/mfc-com.md)

