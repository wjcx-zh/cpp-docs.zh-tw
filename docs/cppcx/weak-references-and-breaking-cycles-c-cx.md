---
title: 弱式參考與中斷循環 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 19252b8684eade131394e98dc705f2f1d451f0cf
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237103"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>弱式參考與中斷循環 (C++/CX)

以參考計數為基礎的類型系統有一個問題，就是對類型的參考會形成「 *循環*」(Cycles)，也就是說，一個物件參考第二個物件、第二個參考第三個物件，以此類推，直到某個最終物件再度參考第一個物件。 在循環中，當一個物件的參考計數變成零時，將無法正確刪除物件。 若要協助您解決這個問題，C + + /CX 提供[platform:: weakreference 類別](../cppcx/platform-weakreference-class.md)類別。 `WeakReference` 物件支援 [Resolve](../cppcx/platform-weakreference-class.md#resolve) 方法。如果物件不再存在，這個方法會傳回 null；如果物件存在但其類型不是 [，則會擲回](../cppcx/platform-invalidcastexception-class.md) Platform::InvalidCastException `T`。

必須使用 `WeakReference` 的其中一個情況，是在用來定義事件處理常式的 Lambda 運算式中擷取 `this` 指標時。 建議您在定義事件處理常式時使用具名方法，但是如果您想為自己的事件處理常式使用 Lambda，或必須在其他某些情況下中斷參考計數循環，則使用 `WeakReference`。 以下為範例：

```

using namespace Platform::Details;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Input;
using namespace Windows::UI::Xaml::Controls;

Class1::Class1()
{
    // Class1 has a reference to m_Page
    m_Page = ref new Page();

    // m_Page will have a reference to this Class1
    // so create a weak reference to this
    WeakReference wr(this);
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)
    {
       // Use the weak reference to get the object
       Class1^ c = wr.Resolve<Class1>();
       if (c != nullptr)
       {
           c->m_eventFired = true;
       }
       else
       {
           // Inform the event that this handler should be removed
           // from the subscriber list
           throw ref new DisconnectedException();
       }
    });
}

}
```

當事件處理常式擲回 `DisconnectedException`時，將會導致事件從訂閱者清單中移除此處理常式。
