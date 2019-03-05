---
title: 建立 OLE 應用程式的作業順序
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b7fa989d1a3b799cf6b427e27142d4479be900bf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263568"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>建立 OLE 應用程式的作業順序

下表顯示您的角色和架構的角色建立 OLE 連結和內嵌的應用程式。 這些代表可用的選項而不是一連串的步驟執行。

### <a name="creating-ole-applications"></a>建立 OLE 應用程式

|工作|您會做|架構會做|
|----------|------------|------------------------|
|建立 COM 元件。|執行 MFC 應用程式精靈。 選擇**全伺服器**或是**迷你伺服**中**複合文件支援** 索引標籤。|架構會啟用 COM 元件的功能產生基本架構的應用程式。 所有的 COM 功能可以傳輸只稍微修改一下後您現有的應用程式。|
|從頭開始建立容器應用程式。|執行 MFC 應用程式精靈。 選擇**容器**中**複合文件支援**] 索引標籤。使用 [類別檢視，請移至原始碼程式碼編輯器。 填寫您的 COM 處理常式函式的程式碼。|架構會產生一個基本架構的應用程式，可以插入 COM 元件 （伺服器） 應用程式所建立的 COM 物件。|
|建立從零開始支援自動化的應用程式。|執行 MFC 應用程式精靈。 選擇**自動化**從**進階功能**] 索引標籤。您可以使用 [類別檢視來公開方法和自動化應用程式中的屬性。|架構會產生可以啟動並由其他應用程式自動化的基本架構應用程式。|

## <a name="see-also"></a>另請參閱

[在架構上建置](../mfc/building-on-the-framework.md)<br/>
[建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)
