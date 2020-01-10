---
title: CWordArray 類別
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907904"
---
# <a name="cwordarray-class"></a>CWordArray 類別

支援 16 位元字組陣列。

## <a name="syntax"></a>語法

```
class CWordArray : public CObject
```

## <a name="members"></a>成員

的成員`CWordArray`函式類似于[CObArray](../../mfc/reference/cobarray-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 只要您看到[CObject](../../mfc/reference/cobject-class.md)指標做為函式參數或傳回值，請以單字取代。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 Null。|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CObArray：： operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CWordArray`併入[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏，以支援其元素的序列化和傾印。 如果將單字陣列儲存到封存中（不論是使用多載插入運算子或具有[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)成員函式），則每個專案都會依次序列化。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要陣列中個別元素的傾印，您必須將傾印內容的深度設定為1或更大。

如需有關使用`CWordArray`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

##  <a name="icommandsource_interface"></a>ICommandSource 介面

管理從命令來源物件傳送到使用者控制項的命令。

```
interface class ICommandSource
```

### <a name="remarks"></a>備註

當您在 MFC 視圖中裝載使用者控制項時， [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)會將命令和更新命令 UI 訊息傳送至使用者控制項，讓它可以處理 MFC 命令（例如，框架功能表項目和工具列按鈕）。 藉由執行，您可以為使用者控制項提供`ICommandSource`物件的參考。

請參閱[How to:將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) ，以取得如何使用`ICommandTarget`的範例。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="addcommandhandler"></a>ICommandSource：： AddCommandHandler

將命令處理常式加入至命令來源物件。

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdHandler*<br/>
命令處理常式方法的控制碼。

### <a name="remarks"></a>備註

這個方法會將命令處理常式*cmdHandler*新增至命令來源物件，並將處理常式對應至*cmdID*。

請參閱[How to:將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) ，以取得如何使用`AddCommandHandler`的範例。

##  <a name="addcommandrangehandler"></a>ICommandSource：： AddCommandRangeHandler

將一組命令處理常式加入至命令來源物件。

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。

*cmdIDMax*<br/>
命令識別碼範圍的結束索引。

*cmdHandler*<br/>
訊息處理常式方法的控制碼，其對應至命令。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令識別碼對應至單一訊息處理常式，並將它新增至命令來源物件。 這是用來處理一組具有一種方法的相關按鈕。

##  <a name="addcommandrangeuihandler"></a>ICommandSource：： AddCommandRangeUIHandler

將使用者介面命令訊息處理常式群組新增至命令來源物件。

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。

*cmdIDMax*<br/>
命令識別碼範圍的結束索引。

*cmdHandler*<br/>
訊息處理常式方法的控制碼，其對應至命令。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令識別碼對應至單一使用者介面命令訊息處理常式，並將它新增至命令來源物件。 這是用來處理一組具有一種方法的相關按鈕。

##  <a name="addcommanduihandler"></a>ICommandSource：： AddCommandUIHandler

將使用者介面命令訊息處理常式加入至命令來源物件。

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdUIHandler*<br/>
使用者介面命令訊息處理常式方法的控制碼。

### <a name="remarks"></a>備註

這個方法會將使用者介面命令訊息處理常式*cmdHandler*加入至命令來源物件，並將處理常式對應至*cmdID*。

##  <a name="postcommand"></a>ICommandSource：:P ostCommand

張貼訊息，而不等候處理。

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要張貼之訊息的命令識別碼。

### <a name="remarks"></a>備註

這個方法會以非同步方式張貼對應至*命令*所指定之識別碼的訊息。 它會呼叫[CWnd：:P ostmessage](../../mfc/reference/cwnd-class.md#postmessage) ，將訊息放在視窗的訊息佇列中，然後傳回而不等待對應的視窗處理訊息。

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

從命令來源物件移除命令處理常式。

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

這個方法會從命令來源物件移除對應至*cmdID*的命令處理常式。

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

從命令來源物件移除一組命令處理常式。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。

*cmdIDMax*<br/>
命令識別碼範圍的結束索引。

### <a name="remarks"></a>備註

這個方法會從命令來源物件中，移除對應至*cmdIDMin*和*cmdIDMax*所指定命令識別碼的訊息處理常式群組。

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

從命令來源物件移除使用者介面命令訊息處理常式群組。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令識別碼範圍的開始索引。

*cmdIDMax*<br/>
命令識別碼範圍的結束索引。

### <a name="remarks"></a>備註

這個方法會從命令來源物件中，移除一組使用者介面命令訊息處理常式，並對應至*cmdIDMin*和*cmdIDMax*所指定的命令識別碼。

##  <a name="removecommanduihandler"></a>ICommandSource：： RemoveCommandUIHandler

從命令來源物件移除使用者介面命令訊息處理常式。

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

這個方法會從命令來源物件移除對應至*cmdID*的使用者介面命令訊息處理常式。

##  <a name="sendcommand"></a>ICommandSource：： SendCommand

傳送訊息，並等候它在傳回之前處理。

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要傳送之訊息的命令識別碼。

### <a name="remarks"></a>備註

這個方法會以同步方式傳送對應至*命令*所指定之識別碼的訊息。 它會呼叫[CWnd：： SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)將訊息放在視窗的訊息佇列中，並等到該視窗程式在傳回之前處理訊息。

##  <a name="icommandtarget_interface"></a>ICommandTarget 介面

提供具有介面的使用者控制項，以從命令來源物件接收命令。

```
interface class ICommandTarget
```

### <a name="remarks"></a>備註

當您在 MFC 視圖中裝載使用者控制項時， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)會將命令和更新命令 UI 訊息傳送至使用者控制項，讓它可以處理 MFC 命令（例如，框架功能表項目和工具列按鈕）。 藉由`ICommandTarget`執行，您可以為使用者控制項提供物件的參考。

請參閱[How to:將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) ，以取得如何使用`ICommandTarget`的範例。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="initialize"></a>  ICommandTarget::Initialize

初始化命令目標物件。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>參數

*cmdSource*<br/>
命令來源物件的控制碼。

### <a name="remarks"></a>備註

當您在 MFC 視圖中裝載使用者控制項時， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)會將命令和更新命令 UI 訊息傳送至使用者控制項，讓它能夠處理 MFC 命令。

這個方法會初始化命令目標物件，並將它與指定的命令來源物件*cmdSource*產生關聯。 它應該在使用者控制項類別的執行中呼叫。 在初始化時，您應該在`Initialize`執行中呼叫[ICommandSource：： AddCommandHandler](../../mfc/reference/icommandsource-interface.md) ，以命令來源物件註冊命令處理常式。 請參閱[How to:將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) ，以取得如何使用`Initialize`來執行這項操作的範例。

##  <a name="icommandui_interface"></a>ICommandUI 介面

管理使用者介面命令。

```
interface class ICommandUI
```

### <a name="remarks"></a>備註

這個介面提供管理使用者介面命令的方法和屬性。 `ICommandUI`類似于[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)，不同之處`ICommandUI`在於用於與 .net 元件相交互操作的 MFC 應用程式。

`ICommandUI`會在衍生類別`ON_UPDATE_COMMAND_UI`中的處理常式內使用。 當應用程式的使用者啟動（選取或按一下）功能表時，每個功能表項目都會顯示為 [已啟用] 或 [已停用]。 每個功能表命令的目標會藉由執行`ON_UPDATE_COMMAND_UI`處理常式來提供這項資訊。 針對應用程式中的每個命令使用者介面物件，使用 [[類別] [Wizard]](mfc-class-wizard.md)或 [**屬性**] 視窗（在**類別檢視**中），為每個處理常式建立訊息對應專案和函式原型。

如需如何`ICommandUI`在命令路由中使用介面的詳細資訊，請[參閱如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

如需如何在 MFC 中管理使用者介面命令的詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

##  <a name="check"></a>ICommandUI：： Check

將此命令的使用者介面專案設定為適當的檢查狀態。

```
property UICheckState Check;
```

### <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 將`Check`設定為下列值：

|詞彙|定義|
|----------|----------------|
|0|複選|
|1|檢查|
|2|設定不定|

##  <a name="continuerouting"></a>ICommandUI::ContinueRouting

告訴命令路由機制繼續將目前的訊息路由傳送到處理程式鏈。

```
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是應該與傳回 FALSE 的[ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex)處理常式搭配使用的 advanced 成員函式。 如需詳細資訊，請參閱[技術提示 TN006：訊息對應](../../mfc/tn006-message-maps.md)。

##  <a name="enabled"></a>ICommandUI：： Enabled

啟用或停用此命令的使用者介面專案。

```
property bool Enabled;
```

### <a name="remarks"></a>備註

這個屬性會啟用或停用此命令的使用者介面專案。 設定`Enabled`為 TRUE 可啟用專案，FALSE 則會停用它。

##  <a name="id"></a>ICommandUI：： ID

取得`ICommandUI`物件所表示之使用者介面物件的識別碼。

```
property unsigned int ID;
```

### <a name="remarks"></a>備註

這個屬性會取得功能表項目、工具列按鈕或`ICommandUI`物件所表示的其他使用者介面物件的識別碼（控制碼）。

##  <a name="index"></a>ICommandUI：： Index

取得`ICommandUI`物件所表示之使用者介面物件的索引。

```
property unsigned int Index;
```

### <a name="remarks"></a>備註

這個屬性會取得功能表項目、工具列按鈕或`ICommandUI`物件所表示的其他使用者介面物件的索引（控制碼）。

##  <a name="radio"></a>ICommandUI：：收音機

將此命令的使用者介面專案設定為適當的檢查狀態。

```
property bool Radio;
```

### <a name="remarks"></a>備註

這個屬性會將此命令的使用者介面專案設定為適當的檢查狀態。 設定`Radio`為 TRUE 以啟用此專案，否則為 FALSE。

##  <a name="text"></a>ICommandUI：： Text

設定此命令之使用者介面專案的文字。

```
property String^ Text;
```

### <a name="remarks"></a>備註

這個屬性會設定此命令之使用者介面專案的文字。 設定`Text`為文字字串控制碼。

##  <a name="iview_interface"></a>IView 介面

會執行數個[CWinFormsView](../../mfc/reference/cwinformsview-class.md)用來將視圖通知傳送至 managed 控制項的方法。

```
interface class IView
```

### <a name="remarks"></a>備註

`IView`會執行數個`CWinFormsView`方法，以使用將一般視圖通知轉送至裝載的 managed 控制項。 這些是[OnInitialUpdate](../../mfc/reference/iview-interface.md)、 [OnUpdate](../../mfc/reference/iview-interface.md)和[OnActivateView](../../mfc/reference/iview-interface.md)。

`IView`類似于[CView](../../mfc/reference/cview-class.md)，但只能與 managed 視圖和控制項搭配使用。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="onactivateview"></a>IView：： OnActivateView

當 view 已啟動或停用時，由 MFC 呼叫。

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>參數

*activate*<br/>
指出是否正在啟動或停用此視圖。

##  <a name="oninitialupdate"></a>IView：： OnInitialUpdate

在第一次將視圖附加至檔，但在一開始顯示視圖之前，由架構呼叫。

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>IView：： OnUpdate

在修改視圖的檔之後，由 MFC 呼叫。

```
void OnUpdate();
```

### <a name="remarks"></a>備註

此函式可讓視圖更新其顯示以反映修改。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
