---
title: 'event_source (c + + COM 屬性) '
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
ms.openlocfilehash: bea90020c3ec570149e11db95ff6d6f8fd0a5507
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845298"
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

- COM 程式碼的`com` 。 您必須使用 `coclass` when `type` = `com` 。 此值需要您包含下列標頭檔︰

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*優化*<br/>
當 *類型* 為時， `native` 您可以指定 `optimize=size` ，以表示有4個位元組的儲存體 () 類別中所有事件的最小值，或 `optimize=speed` (預設) ，表示有 4 * ( 個位元組的事件) 個位元組的儲存體。

*decorate*<br/>
當 *類型* 為時 `native` ，您可以指定 `decorate=false` ，以表示合併的)  ( 中的展開名稱不應該包含封入類別名稱。 [/Fx](../../build/reference/fx-merge-injected-code.md) 可讓您產生 .mrg 檔案。 `decorate=false`（預設值）會產生合併檔案中的完整類型名稱。

## <a name="remarks"></a>備註

**event_source** C++ 屬性指定要套用它的類別或結構將是事件來源。

**event_source** 是與 [event_receiver](event-receiver.md) 屬性和 [__event](../../cpp/event.md) 關鍵字搭配使用。 用 `event_receiver` 來建立事件接收器。 使用 **`__event`** 事件來源內的方法，將這些方法指定為事件。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass** 時機 `type`=`com`|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[類別屬性](class-attributes.md)
