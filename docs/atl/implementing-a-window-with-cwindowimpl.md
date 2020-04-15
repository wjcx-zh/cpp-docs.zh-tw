---
title: 使用 CWindowImpl 來視窗
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319455"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>使用 CWindowImpl 來視窗

要實現視窗,從`CWindowImpl`派生類。 在派生類中,聲明消息映射和消息處理程式函數。 現在,您可以通過三種不同的方式使用類:

- [建立新的 Windows 類別建立視窗](#_atl_creating_a_window_based_on_a_new_windows_class)

- [超級類現有 Windows 類別](#_atl_superclassing_an_existing_windows_class)

- [子類現有視窗](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>建立新的 Windows 類別建立視窗

`CWindowImpl`包含[DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class)宏來聲明 Windows 類資訊。 此宏實現該`GetWndClassInfo`函數,該函數使用[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)定義新 Windows 類的資訊。 調用`CWindowImpl::Create`時,將註冊此 Windows 類並創建新視窗。

> [!NOTE]
> `CWindowImpl`將 NULL`DECLARE_WND_CLASS`傳遞給宏,這意味著 ATL 將生成 Windows 類名稱。 要指定自己的名稱,請將字串傳遞給`CWindowImpl`派生類中的DECLARE_WND_CLASS。

## <a name="example"></a>範例

下面是一個類的範例,該類基於新的 Windows 類實現視窗:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

要建立視窗,請建立的`CMyWindow`實體,然後調用`Create`方法。

> [!NOTE]
> 要覆蓋預設的 Windows 類`GetWndClassInfo`資訊,`CWndClassInfo`請透過將成員設定為適當的值來實現派生類中的方法。

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>超類現有 Windows 類別

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)宏允許您創建一個視窗,用於超類現有 Windows 類。 在`CWindowImpl`派生類中指定此宏。 與任何其他 ATL 視窗一樣,消息由消息映射處理。

使用DECLARE_WND_SUPERCLASS時,將註冊新的 Windows 類。 此新類將與指定的現有類相同,但會將`CWindowImpl::WindowProc`視窗過程替換為(或使用重寫此方法的函數)。

## <a name="example"></a>範例

下面是一個類的示例,該類對標準 Edit 類進行超類類:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

要建立超類編輯視窗,請創建`CMyEdit`的實例,然後調`Create`用 方法。

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>對現有視窗進行子類別

要對現有視窗進行子類,從`CWindowImpl`派生類並聲明消息映射,如前兩種情況。 但是請注意,您不指定任何 Windows 類信息,因為您將對已存在的視窗進行子類。

而不是呼叫`Create`,`SubclassWindow`呼叫並將其句柄傳遞給要子類的現有視窗。 一旦視窗被子分類,它將使用`CWindowImpl::WindowProc`(或覆蓋此方法的函數)將消息定向到消息映射。 要從物件分離子類別視窗,請呼叫`UnsubclassWindow`。 然後,將還原視窗的原始視窗過程。

## <a name="see-also"></a>另請參閱

[實現視窗](../atl/implementing-a-window.md)
