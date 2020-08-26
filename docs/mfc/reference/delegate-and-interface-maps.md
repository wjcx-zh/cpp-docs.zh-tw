---
title: " (MFC 的委派和介面對應宏) "
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 01f5cbfb1f751823d218761410bc9091b73cb0a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837446"
---
# <a name="delegate-and-interface-map-macros"></a>委派和介面對應巨集

MFC 支援下列委派和介面對應宏：

|名稱|描述|
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|開始委派對應。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|開始介面對應的定義。|
|[CommandHandler 委派](#commandhandler)|向命令來源註冊回呼方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|結束委派對應。|
|[END_INTERFACE_MAP](#end_interface_map)|結束實作檔中的介面對應。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|建立委派對應中的項目。|
|[INTERFACE_PART](#interface_part)|在 BEGIN_INTERFACE_MAP 宏與 END_INTERFACE_MAP 宏之間，用於物件將支援的每個介面。|
|[MAKE_DELEGATE](#make_delegate)|將事件處理常式附加至 managed 控制項。|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

開始委派對應。

### <a name="syntax"></a>語法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>參數

*類*<br/>
裝載 managed 控制項的類別。

### <a name="remarks"></a>備註

此宏會標示委派專案清單的開頭，此專案會撰寫委派對應。 如需如何使用這個宏的範例，請參閱 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>規格需求

**標頭：** msclr\event。h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a> BEGIN_INTERFACE_MAP

在執行檔中使用時，開始介面對應的定義。

### <a name="syntax"></a>語法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
在其中定義介面對應的類別

*baseClass*<br/>
從中衍生 *theClass* 的類別。

### <a name="remarks"></a>備註

針對每個已執行的介面，有一或多個 INTERFACE_PART 宏調用。 針對類別使用的每個匯總，有一個 INTERFACE_AGGREGATE 宏調用。

如需介面對應的詳細資訊，請參閱 [技術附注 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a> CommandHandler 委派

向命令來源註冊回呼方法。

### <a name="syntax"></a>語法

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

這會向命令來源委派註冊回呼方法。 當您將委派加入命令來源物件時，回呼方法會成為來自指定之來源的命令的處理常式。

如需詳細資訊，請參閱 [如何：將命令路由加入至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxwinforms (定義于元件 atlmfc\lib\mfcmifc80.dll) 

## <a name="commanduihandler"></a><a name="commanduihandler"></a> CommandUIHandler

使用使用者介面更新命令訊息來註冊回呼方法。

### <a name="syntax"></a>語法

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdUI*<br/>
命令訊息識別碼。

### <a name="remarks"></a>備註

此委派會使用使用者介面更新命令訊息來註冊回呼方法。 `CommandUIHandler` 類似于 [CommandHandler](#commandhandler) ，不過這個委派會與使用者介面物件更新命令搭配使用。 使用者介面更新命令應該使用訊息處理常式方法與一對一對應。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxwinforms (定義于元件 atlmfc\lib\mfcmifc80.dll) 

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a> END_DELEGATE_MAP

結束委派對應。

### <a name="syntax"></a>語法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>備註

此宏會標示委派專案清單的結尾，而這些專案會撰寫委派對應。 如需如何使用這個宏的範例，請參閱 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>規格需求

**標頭：** msclr\event。h

## <a name="end_interface_map"></a><a name="end_interface_map"></a> END_INTERFACE_MAP

結束實作檔中的介面對應。

### <a name="syntax"></a>語法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>備註

如需介面對應的詳細資訊，請參閱 [技術附注 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a> EVENT_DELEGATE_ENTRY

建立委派對應中的項目。

### <a name="syntax"></a>語法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>參數

*成員*<br/>
要附加到控制項的事件處理常式方法。

*ARG0*<br/>
Managed 事件處理常式方法的第一個引數，例如 `Object^` 。

*ARG1*<br/>
Managed 事件處理常式方法的第二個引數，例如 `EventArgs^` 。

### <a name="remarks"></a>備註

委派對應中的每個專案都對應至 [MAKE_DELEGATE](#make_delegate)所建立的 managed 事件處理常式委派。

### <a name="example"></a>範例

下列程式碼範例示範如何使用 EVENT_DELEGATE_ENTRY 在委派對應中建立 `OnClick` 事件處理常式的專案; 另請參閱 MAKE_DELEGATE 中的程式碼範例。 如需詳細資訊，請參閱 [如何：接收來自原生 c + + 類別的 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>規格需求

**標頭：** msclr\event。h

## <a name="interface_part"></a><a name="interface_part"></a> INTERFACE_PART

在 BEGIN_INTERFACE_MAP 宏與 END_INTERFACE_MAP 宏之間，用於物件將支援的每個介面。

### <a name="syntax"></a>語法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
包含介面對應的類別名稱。
*Iid*<br/>
要對應至內嵌類別的 IID。
*localClass*<br/>
區域類別的名稱。

### <a name="remarks"></a>備註

它可讓您將 IID 對應至 *theClass* 和 *localClass*所表示之類別的成員。

如需介面對應的詳細資訊，請參閱 [技術附注 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a> MAKE_DELEGATE

將事件處理常式附加至 managed 控制項。

### <a name="syntax"></a>語法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>參數

*委託*<br/>
Managed 事件處理常式委派的類型，例如 [EventHandler](/dotnet/api/system.eventhandler)。

*成員*<br/>
要附加至控制項的事件處理常式方法名稱。

### <a name="remarks"></a>備註

此宏會建立型別 *委派* 和名稱 *成員*的 managed 事件處理常式委派。 Managed 事件處理常式委派允許原生類別處理 managed 事件。

### <a name="example"></a>範例

下列程式碼範例示範如何呼叫 `MAKE_DELEGATE` ，以將 `OnClick` 事件處理常式附加至 MFC 控制項 `MyControl` 。 如需此宏在 MFC 應用程式中的運作方式更廣泛的說明，請參閱 [如何：接收來自原生 c + + 類別的 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>規格需求

**標頭：** msclr\event。h

## <a name="see-also"></a>另請參閱

[如何：從原生 c + + 類別接收 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[如何：將命令路由加入至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
