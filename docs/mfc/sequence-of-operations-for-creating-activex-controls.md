---
title: 建立 ActiveX 控制項的作業順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf4c74f2263505ad5d7112021003f92c85a4b84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>建立 ActiveX 控制項的作業順序
下表顯示您的角色和架構的角色建立 ActiveX 控制項 （先前稱為 OLE 控制項）。  
  
### <a name="creating-activex-controls"></a>建立 ActiveX 控制項  
  
|工作|您會做|架構會做|  
|----------|------------|------------------------|  
|建立 ActiveX 控制項架構。|執行 MFC ActiveX 控制項精靈，以建立您的控制項。 在選項頁面中指定所需選項。 選項會包含專案、 授權、 子類別化和 [關於] 方塊方法中的類型和控制項的名稱。|MFC ActiveX 控制項精靈建立 ActiveX 控制項檔案的基本功能，包括來源檔案的應用程式、 控制項和屬性頁或網頁。資源檔。專案檔，與其他人，所有符合您規格。|  
|請參閱控制項和 ActiveX 控制項精靈所提供但不會加入您自己的程式碼行。|建立 ActiveX 控制項和測試使用 Internet Explorer 或[TSTCON 範例](../visual-cpp-samples.md)。|執行中控制項的可調整大小和移動的能力。 它也有**關於方塊**可以叫用的方法 （如果選擇）。|  
|實作控制項的方法和屬性。|加入成員函式來提供公開的介面，以控制項的資料來實作您的控制項特定的方法和屬性。 加入成員變數來保存資料結構，及使用事件處理常式來引發事件，當您決定。|架構已經定義了對應來支援控制項的事件、 屬性和方法，讓您專注於實作的屬性和方法的方式。 預設屬性頁檢視，以及提供預設關於方塊方法。|  
|建構控制項的屬性頁面。|使用 Visual c + + 資源編輯器，以視覺化方式編輯控制項的屬性頁介面：<br /><br /> -建立其他的屬性頁。<br />-建立和編輯點陣圖、 圖示和游標。<br /><br /> 您也可以在對話方塊編輯器中測試的屬性頁面。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。 Visual C++ 可讓您透過輕鬆且視覺化的方式編輯現有的資源並加入新的資源。|  
|測試控制項的事件、 方法和屬性。|重建控制項，並使用測試容器來測試您的處理常式正常運作。|您可以叫用控制項的方法，並使用其透過屬性頁介面或測試容器的屬性。 此外，使用測試容器來追蹤事件引發從控制項和控制項的容器所接收的通知。|  
  
## <a name="see-also"></a>另請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)   
 [建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)

