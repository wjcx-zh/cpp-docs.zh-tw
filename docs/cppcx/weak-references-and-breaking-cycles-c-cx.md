---
title: 弱式參考與中斷循環 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 04ba70c148121de520b470bd727b26e756858011
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214928"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>弱式參考與中斷循環 (C++/CX)

以參考計數為基礎的類型系統有一個問題，就是對類型的參考會形成「 *循環*」(Cycles)，也就是說，一個物件參考第二個物件、第二個參考第三個物件，以此類推，直到某個最終物件再度參考第一個物件。 在循環中，當一個物件的參考計數變成零時，將無法正確刪除物件。 為了協助您解決這個問題，c + +/CX 提供[Platform：： WeakReference 類別](../cppcx/platform-weakreference-class.md)類別。 `WeakReference` 物件支援 [Resolve](../cppcx/platform-weakreference-class.md#resolve) 方法。如果物件不再存在，這個方法會傳回 null；如果物件存在但其類型不是 [，則會擲回](../cppcx/platform-invalidcastexception-class.md) Platform::InvalidCastException `T`。

其中一個 `WeakReference` 必須使用的案例是在 **`this`** 用來定義事件處理常式的 lambda 運算式中捕捉到指標。 建議您在定義事件處理常式時使用具名方法，但是如果您想為自己的事件處理常式使用 Lambda，或必須在其他某些情況下中斷參考計數循環，則使用 `WeakReference`。 以下為範例：

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
