---
title: event_source （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167065"
---
# <a name="event_source"></a>event_source

建立事件來源。

## <a name="syntax"></a>語法

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>參數

*type*<br/>
下列其中一個值的列舉：

- Unmanaged C/C++ 程式碼的`native` (Unmanaged 類別的預設值)。

- COM 程式碼的`com` 。 `type`=`com`時，您必須使用 `coclass`。 此值需要您包含下列標頭檔︰

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
當*type*是 `native`時，您可以指定 `optimize=size`，以指出類別或 `optimize=speed` （預設值）中所有事件有4個位元組的儲存體（最小值），表示有 4 * （事件數目）個位元組的儲存體。

*decorate*<br/>
當*type*是 `native`時，您可以指定 `decorate=false`，以指出合併（. .mrg）檔案中的展開名稱不應該包含封入類別名稱。 [/Fx](../../build/reference/fx-merge-injected-code.md) 可讓您產生 .mrg 檔案。 `decorate=false`（預設值）會產生合併檔案中的完整類型名稱。

## <a name="remarks"></a>備註

**event_source** C++ 屬性指定要套用它的類別或結構將是事件來源。

**event_source** 是與 [event_receiver](event-receiver.md) 屬性和 [__event](../../cpp/event.md) 關鍵字搭配使用。 使用 `event_receiver` 建立事件接收器。 在事件來源中的方法上使用 **__event** ，將這些方法指定為事件。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|`type`=時的**coclass** `com`|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[類別屬性](class-attributes.md)
