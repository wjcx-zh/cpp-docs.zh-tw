---
title: "MFC ActiveX 控制項： 從方法傳回錯誤碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5563153cdc5d90bc522c1f0b4edf48a8cc280755
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控制項：從方法傳回錯誤碼
本文說明如何從 ActiveX 控制項方法傳回錯誤碼。  
  
 若要指出方法內，已發生錯誤，您應該使用[colecontrol:: Throwerror](../mfc/reference/colecontrol-class.md#throwerror)成員函式，其採用`SCODE`（狀態碼） 做為參數。 您可以使用預先定義的 `SCODE` 或自行定義一個。  
  
> [!NOTE]
>  `ThrowError` 原本只用來做為從屬性的 Get 或 Set 函式內或 Automation 方法傳回錯誤的方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。  
  
 針對最常見預先定義的 helper 函式存在`SCODE`s，例如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted)。  
  
 取得一份預先定義`SCODE`s 以及定義自訂的相關指示`SCODE`s，請參閱節[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控制項： 進階主題。  
  
 如需回報程式碼的其他區域中的例外狀況的詳細資訊，請參閱[colecontrol:: Fireerror](../mfc/reference/colecontrol-class.md#fireerror)和區段[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)在 ActiveX 控制項： 進階主題。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

