---
title: "MFC ActiveX 控制項：存取環境屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項, 存取環境屬性"
  - "屬性 [MFC], 存取環境"
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控制項：存取環境屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論 ActiveX 控制項如何存取它的容器控制項的環境屬性。  
  
 控制項可以存取容器的環境屬性取得相對於其容器的資訊。  這些屬性會公開視覺特性，例如容器的背景色彩、容器使用的目前字型和作業特性，例如容器是否在使用者模式或設計工具模式。  控制項可以使用環境屬性為其外觀和行為適合它的內嵌特定容器。  不過，控制項不應假設，它的容器中支援特定環境屬性。  事實上，某些容器可能不支援任何環境屬性。  在沒有環境屬性時，控制項應該假設合理的預設值。  
  
 若要存取環境屬性，請呼叫 [COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md)。  這個函式預期環境屬性的分派 ID 做為第一個參數 \(檔案 OLECTL.H 定義分派標準的 ID 環境屬性 \(Ambient Property\)。  
  
 `GetAmbientProperty` 函式的參數是分派 ID、不同的標記表示預期的屬性型別和指標應傳回值的記憶體。  這個指標參考的資料型別是根據不同的標記會有所不同。  函式傳回 **TRUE** ，如果容器支援屬性，否則會傳回 **FALSE**。  
  
 下列程式碼範例會取得名為「UserMode 的環境屬性的值。如果屬性不是由容器支援，預設值 **TRUE** 假設:  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/CPP/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 對於您的便利 `COleControl` ，提供存取許多常用的環境屬性並傳回適當的預設的 Helper 函式，當屬性是 null 時。  這些 Helper 函式如下:  
  
-   [COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)  
  
-   [AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)  
  
-   [AmbientFont](../Topic/COleControl::AmbientFont.md)  
  
    > [!NOTE]
    >  呼叫端必須呼叫所傳回的字型的 **Release\( \)** 。  
  
-   [AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)  
  
-   [AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)  
  
-   [AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)  
  
-   [AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)  
  
-   [AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)  
  
-   [AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)  
  
-   [AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)  
  
-   [AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)  
  
 如果環境屬性的值變更 \(透過容器的一些動作\)，控制項 **OnAmbientPropertyChanged** 成員函式呼叫。  覆寫這個成員函式來處理這類通知。  **OnAmbientPropertyChanged** 的參數是受影響的環境屬性的分派 ID。  這個分派 ID 的值可能是 **DISPID\_UNKNOWN**，指出一或多個環境屬性已變更，不過，資訊會影響屬性。無法使用。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)