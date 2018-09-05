---
title: 實作使用 CWindowImpl 視窗 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CWindowImpl
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2333c56586d20bc5ec114b8ea8a8811e72fcd755
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763415"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>實作使用 CWindowImpl 視窗

若要實作一個視窗，衍生的類別`CWindowImpl`。 在衍生類別中，宣告訊息對應和訊息處理常式函式。 您現在可以使用您的類別，以三個不同的方式：

- [建立新的 Windows 類別為基礎的視窗](#_atl_creating_a_window_based_on_a_new_windows_class)

- [超級類別現有的 Windows 類別](#_atl_superclassing_an_existing_windows_class)

- [子類別化現有視窗](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 建立新的 Windows 類別為基礎的視窗

`CWindowImpl` 包含[{2&gt;declare_wnd_class&lt;2](reference/window-class-macros.md#declare_wnd_class)巨集來宣告 Windows 類別資訊。 這個巨集實作`GetWndClassInfo`函式，以使用[CWndClassInfo](../atl/reference/cwndclassinfo-class.md)定義新的 Windows 類別的資訊。 當`CWindowImpl::Create`呼叫時，此 Windows 註冊類別並建立新的視窗。

> [!NOTE]
>  `CWindowImpl` 傳遞 NULL 給`DECLARE_WND_CLASS`巨集，這表示 ATL 會產生 Windows 類別名稱。 若要指定您自己的名稱，請將字串傳遞給 {2&gt;declare_wnd_class&lt;2 中您`CWindowImpl`-衍生的類別。

## <a name="example"></a>範例

以下是實作新的 Windows 類別為基礎的視窗類別的範例：

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

若要建立一個視窗，建立的執行個體`CMyWindow`，然後呼叫`Create`方法。

> [!NOTE]
>  若要覆寫預設的 Windows 類別資訊，請實作`GetWndClassInfo`藉由設定衍生類別中的方法`CWndClassInfo`為適當值的成員。

##  <a name="_atl_superclassing_an_existing_windows_class"></a> Superclassing 現有的 Windows 類別

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass)巨集可讓您建立一個視窗，是現有的 Windows 類別。 指定此巨集，在您`CWindowImpl`-衍生的類別。 像其他 ATL 視窗的訊息對應處理訊息。

當您使用 DECLARE_WND_SUPERCLASS 時，將會登錄新的 Windows 類別。 這個新類別會為您指定，但將會取代具有的視窗程序的現有類別相同`CWindowImpl::WindowProc`（或您的函式會覆寫此方法）。

## <a name="example"></a>範例

下列是類別的範例，是標準編輯類別：

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

若要建立 superclass 的 [編輯] 視窗，建立的執行個體`CMyEdit`，然後呼叫`Create`方法。

##  <a name="_atl_subclassing_an_existing_window"></a> 子類別化現有視窗

子類別化現有視窗，衍生的類別`CWindowImpl`並宣告訊息對應，如前兩個案例所示。 不過，要注意的是，您不指定任何 Windows 類別的資訊，因為您將子類別化現有視窗。

而不是呼叫`Create`，呼叫`SubclassWindow`並傳遞至您想要子類別化現有的視窗控制代碼。 一旦子類別化視窗的是，它會使用`CWindowImpl::WindowProc`（或您的函式會覆寫此方法），將導向至訊息對應的訊息。 若要中斷連結子類別的視窗，從您的物件，請呼叫`UnsubclassWindow`。 然後將還原視窗的原始視窗程序。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)

