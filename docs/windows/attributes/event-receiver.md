---
title: event_receiver （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: e483ece1019d4a8203215eddbc4d3b9d545328a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663180"
---
# <a name="eventreceiver"></a>event_receiver

建立事件接收器 (接收)。

## <a name="syntax"></a>語法

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>參數

*type*<br/>
下列其中一個值的列舉：

- `native` unmanaged C/c + + 程式碼 （原生類別的預設值）。

- COM 程式碼的`com` 。 此值需要您包含下列標頭檔︰

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
指定*event_receiver*只有當`type` = **com**。 *layout_dependent*是布林值：

- **true**表示委派的簽章的事件接收者必須完全符合的所要攔截在事件來源中。 接收器事件處理常式的名稱必須符合相關的事件來源介面中指定的名稱。 您必須使用`coclass`時*layout_dependent*是**true**。 會指定稍微更有效率 **，則為 true**。

- **false** （預設值） 表示，呼叫慣例和儲存體類別 (虛擬、 靜態等等) 不需要符合事件方法和處理常式，也不執行處理常式的名稱必須符合事件來源介面的方法名稱。

## <a name="remarks"></a>備註

**Event_receiver** c + + 屬性指定的類別或結構會套用它將是事件接收器，使用 Visual c + + 一致的事件模型。

**event_receiver**搭配[event_source](event-source.md)屬性並[__hook](../../cpp/hook.md)並[__unhook](../../cpp/unhook.md)關鍵字。 使用`event_source`建立事件來源。 使用 **__hook**事件接收器的方法產生關聯的事件來源的事件 （「 攔截 」） 事件接收者方法內。 使用 **__unhook**中斷與它們的關聯。

*event_receiver*只會指定用於 COM 事件接收器 (`type`=**com**)。 預設值*event_receiver*是**false**。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|`coclass` 當*event_receiver*=**，則為 true**|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[類別屬性](class-attributes.md)