---
title: "MFC ActiveX 控制項： 存取環境屬性 |Microsoft 文件"
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
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05e6d37a0550cf157dcd43a22689c9db029b51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX 控制項：存取環境屬性
本文將討論如何 ActiveX 控制項可以存取其控制項容器之環境的屬性。  
  
 控制項可以藉由存取容器的環境屬性取得其容器的相關資訊。 這些屬性會公開視覺特性，例如容器的背景色彩，例如容器目前是否在使用者模式或設計工具模式中，容器和操作特性，所使用的目前字型。 控制項可以使用環境屬性來自訂其外觀和行為，它內嵌的特定容器。 不過，控制項應該永遠不會假設其容器會支援任何特定的環境屬性中。 事實上，某些容器可能不完全支援任何環境屬性。 環境的屬性不存在，控制項應該假設合理的預設值。  
  
 若要存取環境屬性，請呼叫[COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty)。 這個函式會將環境屬性的分派識別碼的第一個參數 (olectl。H 定義的一組標準的環境屬性的分派 Id）。  
  
 參數的`GetAmbientProperty`函式會分派識別碼，表示預期的屬性類型，以及一個指向記憶體 variant 標記值應該會傳回。 此指標所參考的資料型別會根據 variant 標記而有所不同。 此函數會傳回**TRUE**如果容器支援屬性，否則它會傳回**FALSE**。  
  
 下列程式碼範例會取得值的環境的屬性稱為 「 使用者 」 模式。 如果屬性不支援容器，預設值是**TRUE**假設：  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 為了方便起見，`COleControl`提供存取許多常用的環境屬性，並傳回適當的預設值，屬性無法使用時的協助程式函式。 這些 helper 函式如下所示：  
  
-   [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)  
  
-   [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)  
  
-   [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)  
  
    > [!NOTE]
    >  呼叫端必須呼叫**Release （)**上傳回的字型。  
  
-   [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)  
  
-   [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)  
  
-   [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)  
  
-   [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)  
  
-   [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)  
  
-   [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)  
  
-   [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)  
  
-   [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)  
  
 如果環境屬性的值變更 （透過某些動作的容器）、 **OnAmbientPropertyChanged**呼叫控制項的成員函式。 覆寫此成員函式，來處理這類通知。 參數**OnAmbientPropertyChanged**受影響的環境屬性的分派識別碼。 這個分派 ID 的值可能是**DISPID_UNKNOWN**，表示一或多個環境的屬性已變更，但屬性所影響的資訊無法使用。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

