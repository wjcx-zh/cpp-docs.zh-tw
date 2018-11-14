---
title: 委派和介面對應巨集 (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: cd1f38236baf2caca9f2a2a426f28f797291fb13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524647"
---
# <a name="delegate-and-interface-map-macros"></a>委派和介面對應巨集

MFC 支援委派和介面對應這些巨集：

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|開始委派對應。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|開始 interfaced 對應的定義。|
|[CommandHandler 委派](#commandhandler)|向命令來源註冊回呼方法。  |
|[END_DELEGATE_MAP](#end_delegate_map)|結束委派對應。|
|[END_INTERFACE_MAP](#end_interface_map)|結束實作檔中的介面對應。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|建立委派對應中的項目。|
|[INTERFACE_PART](#interface_part)|BEGIN_INTERFACE_MAP 巨集和 END_INTERFACE_MAP 巨集之間用於每個物件將支援的介面。|
|[MAKE_DELEGATE](#make_delegate)|將事件處理常式附加至受管理的控制項。|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

開始委派對應。

### <a name="syntax"></a>語法

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>參數

*類別*<br/>
在其中裝載 managed 的控制項類別。

### <a name="remarks"></a>備註

這個巨集標記的委派項目，撰寫委派對應清單的開頭。 如需如何使用這個巨集的範例，請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標頭：** msclr\event.h

### <a name="see-also"></a>另請參閱

[如何：從原生 C++ 類別接收 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

開始在實作檔中使用時 interfaced 對應的定義。

### <a name="syntax"></a>語法

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>參數

*theClass*<br/>
在其中定義介面對應的類別

*baseClass*<br/>
從中的類別*theClass*衍生自。

### <a name="remarks"></a>備註

每個介面實作，沒有一或多個 INTERFACE_PART 巨集引動過程。 此類別會使用每個彙總，沒有一個 INTERFACE_AGGREGATE 巨集引動過程。

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

如需詳細資訊，請參閱 <<c0> [ 如何： 新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）

### <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

##  <a name="commanduihandler"></a>CommandUIHandler

註冊具有使用者介面更新命令訊息的回呼方法。

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

這個委派會向使用者介面更新命令訊息的回呼方法。 `CommandUIHandler` 類似於[CommandHandler](#commandhandler)不同之處在於這個委派會搭配使用者介面物件更新命令。 使用者介面更新命令應該是一對一的對應訊息處理常式方法。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）

### <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

結束委派對應。

### <a name="syntax"></a>語法

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>備註

這個巨集標記的委派項目，撰寫委派對應清單的結尾。 如需如何使用這個巨集的範例，請參閱[EVENT_DELEGATE_ENTRY](#event_delegate_entry)。

### <a name="requirements"></a>需求

**標頭：** msclr\event.h

### <a name="see-also"></a>另請參閱

[如何：從原生 C++ 類別接收 Windows Forms 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

結束實作檔中的介面對應。

### <a name="syntax"></a>語法

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>備註

如需介面對應的詳細資訊，請參閱[技術提示 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[BEGIN_INTERFACE_MAP](#begin_interface_map)

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

建立委派對應中的項目。

### <a name="syntax"></a>語法

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>參數

*成員*<br/>
要附加到控制項的事件處理常式方法。

*ARG0*<br/>
第一個引數，managed 的事件處理常式方法，例如`Object^`。

*ARG1*<br/>
第二個引數的 managed 的事件處理常式方法，例如`EventArgs^`。

### <a name="remarks"></a>備註

在委派對應中的每個項目對應至所建立的受管理的事件處理常式委派[MAKE_DELEGATE](#make_delegate)。

### <a name="example"></a>範例

下列程式碼範例示範如何建立委派對應中的項目使用 EVENT_DELEGATE_ENTRY`OnClick`事件處理常式; 也請參閱 MAKE_DELEGATE 的程式碼範例。 如需詳細資訊，請參閱 <<c0> [ 如何： 從原生 c + + 類別接收 Windows Form 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>需求

**標頭：** msclr\event.h

### <a name="see-also"></a>另請參閱

[MAKE_DELEGATE](#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)

##  <a name="interface_part"></a>INTERFACE_PART

BEGIN_INTERFACE_MAP 巨集和 END_INTERFACE_MAP 巨集之間用於每個物件將支援的介面。

### <a name="syntax"></a>語法

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
包含介面對應的類別名稱。
*iid*<br/>
要對應到內嵌類別的 IID。
*localClass*<br/>
區域類別的名稱。

### <a name="remarks"></a>備註

它可讓您將 IID 對應至所指定的類別成員*theClass*並*localClass*。

如需有關介面對應的詳細資訊，請參閱[技術提示 38](../tn038-mfc-ole-iunknown-implementation.md)。

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

將事件處理常式附加至受管理的控制項。

### <a name="syntax"></a>語法

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>參數

*委派*<br/>
委派型別之受管理的事件處理常式，如[事件處理常式](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True)。

*成員*<br/>
要附加至控制項的事件處理常式方法的名稱。

### <a name="remarks"></a>備註

這個巨集建立受控的事件處理常式委派型別的*委派*和名稱*成員*。 Managed 的事件處理常式委派可讓原生的類別，以處理受管理的事件。

### <a name="example"></a>範例

下列程式碼範例示範如何呼叫`MAKE_DELEGATE`附加`OnClick`MFC 控制項的事件處理常式`MyControl`。 如需此巨集的 MFC 應用程式中的運作方式的更廣泛說明，請參閱[如何： 從原生 c + + 類別接收 Windows Form 事件](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>需求

**標頭：** msclr\event.h

### <a name="see-also"></a>另請參閱

[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](#event_delegate_entry)

