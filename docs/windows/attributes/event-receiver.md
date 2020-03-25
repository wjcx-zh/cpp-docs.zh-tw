---
title: event_receiver （C++ COM 屬性）
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
ms.openlocfilehash: 9653a0b5c756857d92914496b9c5c6f8aee56ebb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167078"
---
# <a name="event_receiver"></a>event_receiver

建立事件接收器 (接收)。

## <a name="syntax"></a>語法

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>參數

*type*<br/>
下列其中一個值的列舉：

- 適用于非受控 CC++ /code 的 `native` （原生類別的預設值）。

- COM 程式碼的`com` 。 此值需要您包含下列標頭檔︰

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
只有在 `type`=**com**時，才指定*layout_dependent* 。 *layout_dependent*是布林值：

- **true**表示事件接收器中的委派簽章必須與其在事件來源中連結的簽章完全相符。 事件接收器處理常式名稱必須符合相關事件來源介面中指定的名稱。 當*layout_dependent*為**true**時，您必須使用 `coclass`。 指定**true**會稍微提高效率。

- **false** （預設值）表示呼叫慣例和儲存類別（虛擬、靜態和其他）不需要符合事件方法和處理常式;也不需要與事件來源介面方法名稱相符的處理常式名稱。

## <a name="remarks"></a>備註

**Event_receiver** C++屬性會使用視覺化C++的統一事件模型，指定要套用它的類別或結構將是事件接收器。

**event_receiver**搭配[event_source](event-source.md)屬性和[__hook](../../cpp/hook.md)和[__unhook](../../cpp/unhook.md)關鍵字一起使用。 使用 `event_source` 來建立事件來源。 在事件接收器的方法中使用 **__hook** ，將事件接收器方法與事件來源的事件產生關聯（「攔截」）。 使用 **__unhook**將它們中斷關聯。

僅針對 COM 事件接收器（`type`=**com**）指定*layout_dependent* 。 *Layout_dependent*的預設值為**false**。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|*layout_dependent*=**true**時 `coclass`|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[類別屬性](class-attributes.md)
