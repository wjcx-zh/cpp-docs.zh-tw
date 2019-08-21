---
title: 使用 IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 9684781ba99d96e2c58d450ee0ff892374e33aef
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630590"
---
# <a name="using-idispeventimpl"></a>使用 IDispEventImpl

使用`IDispEventImpl`來處理事件時, 您將需要:

- 從[IDispEventImpl](../atl/reference/idispeventimpl-class.md)衍生您的類別。

- 將事件接收器對應新增至您的類別。

- 使用[SINK_ENTRY](reference/composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)宏, 將專案加入至事件接收對應。

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

下列程式碼會出現在 NotSoSimple 中。 相關的程式碼會以批註來注明:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling 範例](../overview/visual-cpp-samples.md)
