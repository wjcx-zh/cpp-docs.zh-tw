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
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364547"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控制項：從方法傳回錯誤碼

本文說明如何從 ActiveX 控制項方法傳回錯誤碼。

要指示方法內發生錯誤,應使用[COleControl:throwError](../mfc/reference/colecontrol-class.md#throwerror)成員函數,該函數以 SCODE(狀態代碼)為參數。 您可以使用預定義的 SCODE 或定義您自己的 SCODE。

> [!NOTE]
> `ThrowError` 原本只用來做為從屬性的 Get 或 Set 函式內或 Automation 方法傳回錯誤的方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。

說明器函數存在於最常見的預定義的 SCOD 中,例如[COleControl:設定不受支援](../mfc/reference/colecontrol-class.md#setnotsupported)[、COleControl::未受支援](../mfc/reference/colecontrol-class.md#getnotsupported),以及[COleControl:設定不允許](../mfc/reference/colecontrol-class.md#setnotpermitted)。

有關預定義的 SCOD 列表和有關定義自訂 SCOD 的說明,請參閱[ActiveX 控件中的 ActiveX 控制件中的「處理錯誤](../mfc/mfc-activex-controls-advanced-topics.md)」部分:進階主題。

有關在代碼的其他區域中報告異常的詳細資訊,請參閱[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和[ActiveX 控制件中「處理活動X」控件中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)部分:高級主題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
