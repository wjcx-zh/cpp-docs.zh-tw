---
title: 使用 IDispEventSimpleImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 8a5e64093d2687efc6c6c5e9b0ce89402d2b99a4
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630575"
---
# <a name="using-idispeventsimpleimpl"></a>使用 IDispEventSimpleImpl

使用`IDispEventSimpleImpl`來處理事件時, 您將需要:

- 從[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)衍生您的類別。

- 將事件接收器對應新增至您的類別。

- 定義描述事件的[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)結構。

- 使用[SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)宏, 將專案加入至事件接收對應。

- 執行您想要處理的方法。

- 建議並 unadvise 事件來源。

## <a name="example"></a>範例

下列範例顯示如何處理 Word 的`DocumentChange` **應用程式**物件所引發的事件。 這個事件會定義為分配`ApplicationEvents`介面上的方法。

範例來自[ATLEventHandling 範例](../overview/visual-cpp-samples.md)。

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

這個範例會`#import`使用, 從 Word 的型別程式庫產生必要的標頭檔。 如果您想要搭配其他版本的 Word 使用此範例, 您必須指定正確的 mso dll 檔案。 例如, Office 2000 提供了 mso9, 而 OfficeXP 則提供 mso.dll。 這段程式碼已從*pch* (Visual Studio 2017 和更早版本中的*stdafx.h* ) 中簡化:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

此範例中實際使用之類型程式庫的唯一資訊是 Word `Application`物件的 CLSID 和`ApplicationEvents`介面的 IID。 此資訊只會在編譯時期使用。

下列程式碼會以簡單的 .h 顯示。 相關的程式碼會以批註來注明:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

下列程式碼來自簡單的 .cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling 範例](../overview/visual-cpp-samples.md)
