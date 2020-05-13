---
title: MFC ActiveX 控制項：進階屬性實作
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364643"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控制項：進階屬性實作

本文介紹了與在 ActiveX 控件中實現高級屬性相關的主題。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

- [唯讀和只寫屬性](#_core_read2donly_and_write2donly_properties)

- [從屬性傳回錯誤代碼](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>唯讀和只寫屬性

Add 屬性精靈提供了一種快速簡便的方法,用於實現控制項的唯讀或只寫屬性。

#### <a name="to-implement-a-read-only-or-write-only-property"></a>完整讀或只寫屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這會開啟[新增屬性精靈](../ide/names-add-property-wizard.md)。

1. 在 **「屬性名稱」** 框中,鍵入屬性的名稱。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 **「屬性類型」** 框中,為屬性選擇正確的類型。

1. 如果需要唯讀屬性,請清除 Set 函數名稱。 如果需要僅寫入屬性,請清除 Get 函數名稱。

1. 按一下 [完成] 。

執行此操作時,"添加屬性嚮導"將函數插入函數`SetNotSupported``GetNotSupported`或調度映射條目中,以代替正常的"設置"或"Get"函數。

如果要將現有屬性更改為唯讀或只寫,可以手動編輯調度映射,並從控制項類中刪除不必要的「設定」或「Get」函數。

如果希望屬性是有條件唯讀或只寫(例如,僅在控制者在特定模式下運行時),則可以像往常一樣提供"設定"或"Get"函數,並在適當情況下調用`SetNotSupported`或`GetNotSupported`函數。 例如：

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

如果資料成員為`SetNotSupported``m_bReadOnlyMode` **TRUE,** 則此程式碼範例呼叫 。 如果**FALSE**,則屬性設置為新值。

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>從屬性傳回錯誤代碼

要指示在嘗試獲取或設置屬性時發生錯誤,請使用`COleControl::ThrowError`函數,該函數以 SCODE(狀態代碼)為參數。 您可以使用預定義的 SCODE 或定義您自己的 SCODE。 有關預定義的 SCOD 列表和用於定義自訂 SCOD 的說明,請參閱[「ActiveX」控制件中的「處理活動X」控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md):進階主題。

說明器函數存在於最常見的預定義的 SCOD 中,例如[COleControl:設定不受支援](../mfc/reference/colecontrol-class.md#setnotsupported)[、COleControl::未受支援](../mfc/reference/colecontrol-class.md#getnotsupported),以及[COleControl:設定不允許](../mfc/reference/colecontrol-class.md#setnotpermitted)。

> [!NOTE]
> `ThrowError`僅用於用作從屬性的 Get 或 Set 函數或自動化方法中返回錯誤的方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。

有關報告代碼其他區域中的異常的詳細資訊,請參閱[COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)和["ActiveX 控制件中處理"活動X控制中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)"一節:高級主題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)
