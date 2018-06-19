---
title: MFC ActiveX 控制項： 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac9d9e4f5e7d777bd147ce36e970e7a30fd875b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347103"
---
# <a name="mfc-activex-controls-properties"></a>MFC ActiveX 控制項：屬性
ActiveX 控制項就會引發事件，其控制項容器與通訊。 容器會使用方法和屬性與控制項進行通訊。 方法和屬性類似的用途及目的，分別為成員函式和 c + + 類別的成員變數。 屬性是 ActiveX 控制項的任何容器中公開的資料成員。 屬性會提供包含 ActiveX 控制項，例如 Automation 用戶端和 ActiveX 控制項容器應用程式的介面。  
  
 屬性也稱為屬性。  
  
 如需 ActiveX 控制項方法的詳細資訊，請參閱文章[MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)。  
  
 ActiveX 控制項可以實作內建和自訂的方法與屬性。 類別`COleControl`提供內建屬性的實作。 (如內建屬性完整清單，請參閱文章[MFC ActiveX 控制項： 加入內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)。)開發人員所定義的自訂屬性加入至 ActiveX 控制項的特製化的功能。 如需詳細資訊，請參閱[MFC ActiveX 控制項： 加入自訂屬性](../mfc/mfc-activex-controls-adding-custom-properties.md)。  
  
 處理屬性和方法以及現有的成員函式的分派對應所組成的機制可支援自訂及內建屬性，與方法類似，`COleControl`類別。 此外，這些屬性可以有開發人員用來將額外的資訊傳遞給控制項的參數。  
  
 下列文章中討論的更詳細的 ActiveX 控制項屬性：  
  
-   [MFC ActiveX 控制項：新增內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [MFC ActiveX 控制項：新增自訂屬性](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [MFC ActiveX 控制項：進階屬性實作](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [MFC ActiveX 控制項：存取環境屬性](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

