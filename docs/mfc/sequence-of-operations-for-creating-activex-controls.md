---
title: 建立 ActiveX 控制項的作業順序
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: 020c044cc0b3b96df102a5ab6625c945f1033f67
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781337"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>建立 ActiveX 控制項的作業順序

下表顯示您的角色和架構的角色建立 ActiveX 控制項 （先前稱為 OLE 控制項）。

### <a name="creating-activex-controls"></a>建立 ActiveX 控制項

|工作|您會做|架構會做|
|----------|------------|------------------------|
|建立 ActiveX 控制項架構。|執行 MFC ActiveX 控制項精靈，來建立您的控制項。 在選項頁面中指定所需選項。 選項包括專案、 授權、 子類別化和 [關於] 方塊方法中的類型和控制項的名稱。|MFC ActiveX 控制項精靈會建立具有基本功能，包括您的應用程式、 控制項和屬性頁或頁面; 的來源檔案的 ActiveX 控制項的檔案資源檔。專案檔，與其他人，所有符合您的規格。|
|控制項和 ActiveX 控制項精靈能提供什麼而不加入您自己的程式碼行，請參閱。|建立 ActiveX 控制項，並測試它與 Internet Explorer 或[TSTCON 範例](../overview/visual-cpp-samples.md)。|執行中控制項的調整大小和移動的能力。 它也有 **[關於] 方塊**可以叫用的方法 （如果選擇）。|
|實作控制項的方法和屬性。|加入成員函式，以提供控制項的資料的公開的介面來實作您的控制項特定的方法和屬性。 加入成員變數來保存資料結構，並使用事件處理常式來引發事件，當您決定時。|架構已定義的模式，以支援控制項的事件、 屬性和方法，讓您專注於實作的屬性和方法的方式。 [預設] 屬性頁是可檢視，並提供預設的 [關於] 方塊方法。|
|建構控制項的屬性頁面。|使用視覺效果C++資源編輯器，以視覺化方式編輯控制項的屬性頁介面：<br /><br />-建立額外的屬性頁。<br />-建立及編輯點陣圖、 圖示和游標。<br /><br /> 您也可以在對話方塊編輯器中測試的屬性頁面。|MFC 應用程式精靈建立的預設資源檔提供您所需的許多資源。 Visual C++ 可讓您透過輕鬆且視覺化的方式編輯現有的資源並加入新的資源。|
|測試控制項的事件、 方法和屬性。|重建控制項，並使用測試容器來測試您的處理常式，可正確運作。|您可以叫用控制項的方法，並使用其屬性，透過屬性頁介面或測試容器。 此外，使用測試容器，以從控制項所引發的追蹤事件和控制項的容器所收到的通知。|

## <a name="see-also"></a>另請參閱

[在架構上建置](../mfc/building-on-the-framework.md)<br/>
[建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)
