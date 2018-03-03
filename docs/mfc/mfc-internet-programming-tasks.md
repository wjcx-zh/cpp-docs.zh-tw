---
title: "MFC 網際網路程式設計工作 |Microsoft 文件"
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
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd726860e181eb352d7368f31a31d2cbd7489000
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-internet-programming-tasks"></a>MFC 網際網路程式設計工作
本節包含將網際網路支援加入至您應用程式的詳細步驟。 其中的主題包含如何使用 MFC 類別以使您現有的應用程式支援網際網路，以及如何將主動式文件支援加入至現有的 COM 元件。 您要建立包含文件最新股價、 匹茲堡橄欖球分數和南極洲 microsoft 最新溫度提供數個技術可幫助您這樣做，透過網際網路。  
  
 Active 技術包括 ActiveX 控制項 (先前稱為 OLE 控制項) 和 Active 文件；WinInet 可輕鬆地跨網際網路擷取和儲存檔案，而非同步 Moniker 則可以有效率地下載資料。 Visual C++ 提供許多精靈，利用起始應用程式協助您快速入門。 如需這些技術的簡介，請參閱[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)和[MFC COM](../mfc/mfc-com.md)。  
  
 您總是想要透過 FTP 檔案，但是尚未學習 WinSock 和網路程式設計通訊協定 WinInet 類別封裝這些通訊協定，提供一組簡單的函式可用來撰寫用戶端應用程式上網際網路，下載檔案使用 HTTP、 FTP 和 gopher。 您可以使用 WinInet 搜尋您的硬碟或整個世界的目錄。 您可以收集數種不同類型的資料，並將其呈現給整合介面的使用者。  
  
 您有大量的資料需要下載非同步 moniker，請提供大型物件的漸進式呈現的 COM （元件物件模型） 解決方案。 WinInet 也可以透過非同步方式使用。  
  
 下表描述您可以使用這些技術進行的一些事項。  
  
|您有|您想要|您應該|  
|--------------|-----------------|----------------|  
|一部 Web 伺服器。|追蹤與 URL 要求相關的登入和詳細資訊。|撰寫一個篩選器、要求登入事件和 URL 對應的通知。|  
|一個 Web 瀏覽器。|提供動態內容。|建立 ActiveX 控制項和主動式文件。|  
|以文件為基礎的應用程式。|加入透過 FTP 下載檔案的支援。|使用 WinInet 或非同步 Moniker。|  
  
 請參閱下列主題以取得入門的詳細資訊：  
  
-   [應用程式設計選擇](../mfc/application-design-choices.md)  
  
-   [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)  
  
-   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
-   [升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [網際網路上的主動式文件](../mfc/active-documents-on-the-internet.md)  
  
-   [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [測試網際網路應用程式](../mfc/testing-internet-applications.md)  
  
-   [網際網路安全性](../mfc/internet-security-cpp.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [依工作分類的網際網路資訊](../mfc/internet-information-by-task.md)

