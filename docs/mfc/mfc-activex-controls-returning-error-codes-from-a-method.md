---
title: "MFC ActiveX 控制項：從方法傳回錯誤碼 | Microsoft Docs"
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
  - "錯誤 [C++], ActiveX 控制項錯誤碼"
  - "FireError 方法"
  - "GetNotSupported 方法"
  - "MFC ActiveX 控制項, 錯誤碼"
  - "SCODE, MFC ActiveX 控制項"
  - "SetNotSupported 方法, 使用"
  - "ThrowError 方法"
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：從方法傳回錯誤碼
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何從 ActiveX 控制項回傳方法的錯誤碼。  
  
 表示錯誤在方法內發生錯誤，您應該使用 [COleControl::ThrowError](../Topic/COleControl::ThrowError.md) 成員函式，採用 `SCODE` \(狀態碼\) 做為參數。  您可以使用預先定義的 `SCODE` 或自行定義。  
  
> [!NOTE]
>  `ThrowError` 被視為只用來做為傳回錯誤的方法是從屬性取得的內部或 Set 函式或自動化方法。  這些是適當的例外處理常式會出現在堆疊唯一的時候。  
  
 Helper 函式為最常用的預先定義 `SCODE`存在，例如 [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)、 [COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)和 [COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)。  
  
 如需定義自訂 `SCODE`的預先定義 `SCODE`物件的清單，請參閱《ActiveX 控制項的 [在您的 ActiveX 控制項的處理錯誤](../mfc/mfc-activex-controls-advanced-topics.md) 一節:進階主題。  
  
 如需在程式碼的其他區域的報告例外狀況的詳細資訊，請參閱 [COleControl::FireError](../Topic/COleControl::FireError.md) 和區段在 ActiveX 控制項的 [在您的 ActiveX 控制項的處理錯誤](../mfc/mfc-activex-controls-advanced-topics.md) :進階主題。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)