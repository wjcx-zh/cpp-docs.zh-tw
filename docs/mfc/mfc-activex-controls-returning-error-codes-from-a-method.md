---
title: MFC ActiveX 控制項：從方法傳回錯誤碼
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 1f7564d750b476ac3f57656f3392e0801652e5d5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615521"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控制項：從方法傳回錯誤碼

本文說明如何從 ActiveX 控制項方法傳回錯誤碼。

若要指出方法內發生錯誤，您應該使用[COleControl：： ThrowError](reference/colecontrol-class.md#throwerror)成員函式，其採用 SCODE （狀態碼）做為參數。 您可以使用預先定義的 SCODE 或定義您自己的一個。

> [!NOTE]
> `ThrowError` 原本只用來做為從屬性的 Get 或 Set 函式內或 Automation 方法傳回錯誤的方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。

Helper 函式存在於最常見的預先定義 SCODEs，例如[COleControl：： SetNotSupported](reference/colecontrol-class.md#setnotsupported)、 [COleControl：： GetNotSupported](reference/colecontrol-class.md#getnotsupported)和[COleControl：： SetNotPermitted](reference/colecontrol-class.md#setnotpermitted)。

如需預先定義的 SCODEs 和定義自訂 SCODEs 的指示清單，請參閱在 ActiveX 控制項中[處理 Activex 控制項](mfc-activex-controls-advanced-topics.md)中的錯誤一節： Advanced 主題。

如需有關在程式碼的其他區域中報告例外狀況的詳細資訊，請參閱[COleControl：： FireError](reference/colecontrol-class.md#fireerror)和在 activex 控制項中[處理 activex 控制項](mfc-activex-controls-advanced-topics.md)中的錯誤一節： Advanced 主題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
