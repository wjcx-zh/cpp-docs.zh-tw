---
title: MFC ActiveX 控制項： 從方法傳回錯誤碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927915"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控制項：從方法傳回錯誤碼
本文說明如何從 ActiveX 控制項方法傳回錯誤碼。  
  
 若要指出方法內，已發生錯誤，您應該使用[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)成員函式，其採用 SCODE （狀態碼） 做為參數。 您可以使用預先定義的 SCODE 或定義您自己的其中一個。  
  
> [!NOTE]
>  `ThrowError` 原本只用來做為從屬性的 Get 或 Set 函式內或 Automation 方法傳回錯誤的方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。  
  
 Helper 函式存在的最常見預先定義的 SCODEs，例如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[colecontrol:: Setnotpermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 如需預先定義的 SCODEs 以及定義自訂 SCODEs 的相關指示，請參閱下節[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控制項： 進階主題。  
  
 如需回報程式碼的其他區域中的例外狀況的詳細資訊，請參閱[colecontrol:: Fireerror](../mfc/reference/colecontrol-class.md#fireerror)和區段[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控制項： 進階主題。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

