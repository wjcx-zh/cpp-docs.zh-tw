---
title: "MFC ActiveX 控制項：屬性 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 屬性"
  - "屬性 [MFC]"
  - "屬性 [MFC], ActiveX 控制項"
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項引發事件與其控制項容器通訊。  容器，傳回，使用方法和屬性與控制項溝通。  方法和屬性都是在使用中且打算，分別，對成員函式，而且 C \+\+. 的成員變數分類。  屬性是公開到所有容器 ActiveX 控制項的資料成員。  屬性為包含 ActiveX 控制項的應用程式提供的介面，例如 Automation 用戶端和 ActiveX 控制項容器。  
  
 屬性也稱為屬性。  
  
 如需 ActiveX 控制項方法的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項:方法](../mfc/mfc-activex-controls-methods.md)。  
  
 ActiveX 控制項可以實作內建和自訂方法和屬性。  類別為 `COleControl` 內建屬性提供實作。\(如需內建屬性的完整清單，請參閱本文 [MFC ActiveX 控制項:將內建屬性。](../mfc/mfc-activex-controls-adding-stock-properties.md)\)。自訂屬性，定義由開發人員，將特定功能加入至 ActiveX 控制項。  如需詳細資訊，請參閱 [MFC ActiveX 控制項:將自訂屬性](../mfc/mfc-activex-controls-adding-custom-properties.md)。  
  
 自訂和內建屬性，例如方法，由包含分派對應處理屬性，以及方法和現有 `COleControl` 成員函式分類的機制支援。  此外，這些屬性可以有開發人員使用將額外資訊加入控制項的參數。  
  
 下列文件會進一步討論 ActiveX 控制項屬性:  
  
-   [MFC ActiveX 控制項:將內建屬性。](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [MFC ActiveX 控制項:將自訂屬性](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [MFC ActiveX 控制項:進階屬性實作](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [MFC ActiveX 控制項:存取的環境屬性。](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)