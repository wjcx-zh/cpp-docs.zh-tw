---
title: 委派和介面對應宏（MFC）
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856658"
---
# <a name="delegate-and-interface-map-macros"></a>委派和介面對應巨集

MFC 支援委派和介面對應的下列宏：

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|開始委派對應。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|開始介面對應的定義。|
|[CommandHandler 委派](#commandhandler)|向命令來源註冊回呼方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|結束委派對應。|
|[END_INTERFACE_MAP](#end_interface_map)|結束實作檔中的介面對應。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|建立委派對應中的項目。|
|[INTERFACE_PART](#interface_part)|在 BEGIN_INTERFACE_MAP 宏與您的物件將支援之每個介面的 END_INTERFACE_MAP 宏之間使用。|
|[MAKE_DELEGATE](#make_delegate)|將事件處理常式附加至 managed 控制項。|

## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

開始委派對應。

### <a name="syntax"></a>語法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>參數

*課堂*<br/>
主控 managed 控制項的類別。

### <a name="remarks"></a>備註

這個宏會標記委派專案清單的開頭，其組成委派對應。 如需如何使用此宏的範例，請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標頭：** msclr\event。h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

在執行檔中使用時，開始介面對應的定義。

### <a name="syntax"></a>語法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
在其中定義介面對應的類別

*baseClass*<br/>
從中衍生*theClass*的類別。

### <a name="remarks"></a>備註

針對每個已執行的介面，都有一或多個 INTERFACE_PART 宏調用。 針對類別所使用的每個匯總，有一個 INTERFACE_AGGREGATE 宏調用。

如需有關介面對應的詳細資訊，請參閱[技術提示 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="commandhandler"></a>CommandHandler 委派

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

如需詳細資訊，請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**Header：** afxwinforms. h （定義于 assembly atlmfc\lib\mfcmifc80.dll）

##  <a name="commanduihandler"></a>CommandUIHandler

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

此委派會向使用者介面更新命令訊息註冊回呼方法。 `CommandUIHandler` 類似于[CommandHandler](#commandhandler) ，不同之處在于這個委派會與使用者介面物件更新命令搭配使用。 使用者介面更新命令應該與訊息處理常式方法一對一對應。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**Header：** afxwinforms. h （定義于 assembly atlmfc\lib\mfcmifc80.dll）

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

結束委派對應。

### <a name="syntax"></a>語法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>備註

這個宏會標示委派專案清單的結尾，其中會組成委派對應。 如需如何使用此宏的範例，請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標頭：** msclr\event。h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

結束實作檔中的介面對應。

### <a name="syntax"></a>語法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>備註

如需有關介面對應的詳細資訊，請參閱[技術提示 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

建立委派對應中的項目。

### <a name="syntax"></a>語法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>參數

*成員國*<br/>
要附加到控制項的事件處理常式方法。

*ARG0*<br/>
Managed 事件處理常式方法的第一個引數，例如 `Object^`。

*ARG1*<br/>
Managed 事件處理常式方法的第二個引數，例如 `EventArgs^`。

### <a name="remarks"></a>備註

委派對應中的每個專案都會對應到[MAKE_DELEGATE](#make_delegate)所建立的 managed 事件處理常式委派。

### <a name="example"></a>範例

下列程式碼範例示範如何使用 EVENT_DELEGATE_ENTRY，在 `OnClick` 事件處理常式的委派對應中建立專案。另請參閱 MAKE_DELEGATE 中的程式碼範例。 如需詳細資訊，請參閱[如何：接收來自原生C++類別的 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>需求

**標頭：** msclr\event。h

##  <a name="interface_part"></a>INTERFACE_PART

在 BEGIN_INTERFACE_MAP 宏與您的物件將支援之每個介面的 END_INTERFACE_MAP 宏之間使用。

### <a name="syntax"></a>語法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
包含介面對應的類別名稱。
*iid*<br/>
要對應至內嵌類別的 IID。
*localClass*<br/>
本機類別的名稱。

### <a name="remarks"></a>備註

它可讓您將 IID 對應至*theClass*和*localClass*所指示之類別的成員。

如需有關介面對應的詳細資訊，請參閱[技術提示 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

將事件處理常式附加至 managed 控制項。

### <a name="syntax"></a>語法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>參數

*委託人*<br/>
Managed 事件處理常式委派的類型，例如[EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True)。

*成員國*<br/>
要附加至控制項的事件處理常式方法的名稱。

### <a name="remarks"></a>備註

這個宏會建立類型為*delegate*的 managed 事件處理常式委派，以及名稱*成員*的。 Managed 事件處理常式委派可讓原生類別處理 managed 事件。

### <a name="example"></a>範例

下列程式碼範例示範如何呼叫 `MAKE_DELEGATE`，以將 `OnClick` 事件處理常式附加至 MFC 控制項 `MyControl`。 如需此宏在 MFC 應用程式中的運作方式更廣泛的說明，請參閱[如何：接收來自C++原生類別的 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>需求

**標頭：** msclr\event。h

## <a name="see-also"></a>另請參閱

[如何：從原生 C++ 類別接收 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[宏和全域](mfc-macros-and-globals.md)<br/>
