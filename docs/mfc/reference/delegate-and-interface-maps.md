---
title: 委託與介面對應巨集 (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365828"
---
# <a name="delegate-and-interface-map-macros"></a>委派和介面對應巨集

MFC 支援這些巨集進行委託與介面映射:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|開始委託映射。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|開始定義介面映射。|
|[CommandHandler 委派](#commandhandler)|向命令來源註冊回呼方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|結束委託映射。|
|[END_INTERFACE_MAP](#end_interface_map)|結束實作檔中的介面對應。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|建立委派對應中的項目。|
|[INTERFACE_PART](#interface_part)|在BEGIN_INTERFACE_MAP宏和END_INTERFACE_MAP宏之間使用,用於對象將支援的每個介面。|
|[MAKE_DELEGATE](#make_delegate)|將事件處理程式附加到托管控件。|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

開始委託映射。

### <a name="syntax"></a>語法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>參數

*類別*<br/>
托管控件的類。

### <a name="remarks"></a>備註

此宏標記委託條目清單的開頭,該列表組成委託映射。 有關如何使用此宏的範例,請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標題:** msclr_event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

在實現檔中使用時開始定義介面映射。

### <a name="syntax"></a>語法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*類別*<br/>
在其中定義介面對應的類別

*基類*<br/>
類派生自*的*類。

### <a name="remarks"></a>備註

對於實現的每個介面,有一個或多個INTERFACE_PART宏調用。 對於類使用的每個聚合,有一個INTERFACE_AGGREGATE宏調用。

有關介面地圖的詳細資訊,請參閱[技術說明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>命令處理常式

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

有關詳細資訊,請參閱[:將指令路由新增到 Windows 窗體控制件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標題**:afxwinforms.h(在程式集 atlmfc_lib_mfcmc80.dll 中定義)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>命令UIHandler

使用使用者介面更新命令消息註冊回調方法。

### <a name="syntax"></a>語法

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdUI*<br/>
命令消息識別碼。

### <a name="remarks"></a>備註

此委託使用用戶介面更新命令消息註冊回調方法。 `CommandUIHandler`與[CommandHandler](#commandhandler)類似,只不過此委託與使用者介面物件更新命令一起使用。 使用者介面更新命令應使用消息處理程式方法一對一對應。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標題**:afxwinforms.h(在程式集 atlmfc_lib_mfcmc80.dll 中定義)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

結束委託映射。

### <a name="syntax"></a>語法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>備註

此宏標記委託條目清單的末尾,該列表組成委託映射。 有關如何使用此宏的範例,請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標題:** msclr_event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

結束實作檔中的介面對應。

### <a name="syntax"></a>語法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>備註

有關介面對應的詳細資訊,請參閱[技術說明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

建立委派對應中的項目。

### <a name="syntax"></a>語法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>參數

*成員*<br/>
要附加到控制項的事件處理常式方法。

*ARG0*<br/>
託管事件處理程式方法的第一個參數,如`Object^`。

*ARG1*<br/>
託管事件處理程式方法的第二個參數,如`EventArgs^`。

### <a name="remarks"></a>備註

委託映射中的每個條目對應於[由MAKE_DELEGATE](#make_delegate)創建的託管事件處理程式委託。

### <a name="example"></a>範例

以下代碼示例演示如何使用EVENT_DELEGATE_ENTRY在`OnClick`事件處理程序的授權映射中創建條目;另請參閱MAKE_DELEGATE中的代碼示例。 有關詳細資訊,請參閱[:從本機C++類下沉 Windows 窗體事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>需求

**標題:** msclr_event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

在BEGIN_INTERFACE_MAP宏和END_INTERFACE_MAP宏之間使用,用於對象將支援的每個介面。

### <a name="syntax"></a>語法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
包含介面對應的類別名稱。
*Iid*<br/>
要映射到嵌入類的IID。
*localClass*<br/>
本地類的名稱。

### <a name="remarks"></a>備註

它允許您將 IID 映射到*類*和*localClass*指示的類的成員。

有關介面地圖的詳細資訊,請參閱[技術說明 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

將事件處理程式附加到托管控件。

### <a name="syntax"></a>語法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>參數

*委託*<br/>
管理事件處理程式的類型,如[事件處理程式](/dotnet/api/system.eventhandler)。

*成員*<br/>
要附加到控制項的事件處理程式方法的名稱。

### <a name="remarks"></a>備註

此巨集建立類型 *「代表」* 和「*成員*」 名稱的託管事件處理程式委託。 託管事件處理程式委託允許本機類處理託管事件。

### <a name="example"></a>範例

以下代碼示例演示如何調用`MAKE_DELEGATE``OnClick`將事件處理程式附加到 MFC`MyControl`控件。 有關此宏在 MFC 應用程式中工作方式的更廣泛說明,請參閱[:從本機 C++類沉陷 Windows 窗體事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>需求

**標題:** msclr_event.h

## <a name="see-also"></a>另請參閱

[如何：從原生 C++ 類別接收 Windows Form 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
