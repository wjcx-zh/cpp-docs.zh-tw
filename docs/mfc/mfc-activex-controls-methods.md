---
title: "MFC ActiveX 控制項：方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項, 方法"
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項引發事件通訊本身和其控制項容器之間。  容器可以與控制項也通訊方法和屬性。  方法也會呼叫函式。  
  
 方法和屬性提供輸出介面供其他應用程式使用，例如 Automation 用戶端和 ActiveX 控制項容器。  如需 ActiveX 控制項屬性的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:屬性](../mfc/mfc-activex-controls-properties.md)。  
  
 方法類似在使用中且打算至 C \+\+. 類別的成員函式。  將控制項可以實作方法的兩種型別:內建和自訂。  類似於內建事件，內建方法是 [COleControl](../mfc/reference/colecontrol-class.md) 提供實作的方法。  如需內建方法的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:將內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。  自訂方法，定義由開發人員，可以讓控制項的其他自訂。  如需詳細資訊，請參閱文件 [MFC ActiveX 控制項:將自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。  
  
 Microsoft Foundation Class 程式庫 \(MFC\) 實作讓您的控制項支援內建和自訂方法的機制。  第一個部分是類別 `COleControl`。  衍生自 `CWnd`， `COleControl` 成員函式支援對所有 ActiveX 控制項通用的內建方法。  這個機制的第二部分是分派對應。  分派對應類似訊息對應;不過，而不是對應至 Windows 訊息 ID 的函式，分派對應對應虛擬成員函式為 IDispatch IDS。  
  
 若要適當地支援的控制項的各種方法，其類別必須宣告分派對應。  這是由位於控制項類別標頭的下列程式碼完成 \(。H\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/CPP/mfc-activex-controls-methods_1.h)]  
  
 分派對應的主要用途是建立外部呼叫端使用的方法名稱 \(例如或\) 和實作方法的類別的成員函式之間的關聯性。  在分派對應宣告之後，會在控制項的實作 \(.CPP\) 檔案所定義。  下列程式碼會定義分派對應:  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/CPP/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/CPP/mfc-activex-controls-methods_3.cpp)]  
  
 如果您使用 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md) 建立專案，這幾行程式碼會自動加入。  如果未使用 MFC ActiveX 控制項精靈，您必須手動將這些行。  
  
 下列文章詳細討論方法:  
  
-   [MFC ActiveX 控制項:將內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [MFC ActiveX 控制項:將自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [MFC ActiveX 控制項:從方法傳回的錯誤碼](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)