---
title: CWordArray 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: c21f89215e08523188eb32490d7b1d5506299fb5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259447"
---
# <a name="cwordarray-class"></a>CWordArray 類別

支援 16 位元字組陣列。

## <a name="syntax"></a>語法

```
class CWordArray : public CObject
```

## <a name="members"></a>成員

成員函式`CWordArray`類別的成員函式類似[CObArray](../../mfc/reference/cobarray-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論在何處看到[CObject](../../mfc/reference/cobject-class.md)指標做為函式參數或傳回值，取代文字。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 NULL。|
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
|[CObArray::operator &#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CWordArray` 併入[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集，支援序列化和傾印其項目。 如果文字陣列儲存封存，或是利用多載的插入運算子[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)成員函式，每個項目是，進而，序列化。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要個別的項目陣列中的傾印，您必須設定為 1 或更高的傾印內容的深度。

如需有關使用`CWordArray`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

##  <a name="icommandsource_interface"></a>  ICommandSource Interface

管理從命令來源物件傳送至使用者控制項的命令。

```
interface class ICommandSource
```

### <a name="remarks"></a>備註

當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 訊息至使用者控制項讓它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。 藉由實作，您提供的使用者控制項的參考`ICommandSource`物件。

請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`ICommandTarget`。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

將命令來源物件中的命令處理常式。

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdHandler*<br/>
命令處理常式方法的處理常式。

### <a name="remarks"></a>備註

此方法會將命令處理常式*cmdHandler*命令來源物件，並將對應的處理常式*cmdID*。

請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`AddCommandHandler`。

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

將一群命令處理常式加入命令來源物件。

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。

*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

*cmdHandler*<br/>
命令對應至訊息處理常式方法的處理常式。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令 Id 對應至單一訊息處理常式，並將它新增至命令來源物件。 這用來處理使用其中一種方法的一組相關的按鈕。

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

將一群使用者介面的命令訊息處理常式，加入命令來源物件。

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。

*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

*cmdHandler*<br/>
命令對應至訊息處理常式方法的處理常式。

### <a name="remarks"></a>備註

這個方法會將連續範圍的命令 Id 對應至單一使用者介面命令訊息處理常式，並將它新增至命令來源物件。 這用來處理使用其中一種方法的一組相關的按鈕。

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

將命令來源物件中的使用者介面命令訊息處理常式。

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

*cmdUIHandler*<br/>
使用者介面命令訊息處理常式方法的處理常式。

### <a name="remarks"></a>備註

此方法會將使用者介面命令訊息處理常式*cmdHandler*命令來源物件，並將對應的處理常式*cmdID*。

##  <a name="postcommand"></a>  ICommandSource::PostCommand

公佈訊息，而不需等待處理。

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要張貼之訊息的命令識別碼。

### <a name="remarks"></a>備註

這個方法將訊息對應到所指定的識別碼以非同步方式張貼*命令*。 它會呼叫[CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage)放置在視窗的訊息佇列，然後傳回的訊息，而不需等待處理的訊息對應的視窗。

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

移除的命令來源物件中的命令處理常式。

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

這個方法會移除對應至命令處理常式*cmdID*命令來源物件中。

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

移除的命令來源物件中的一群命令處理常式。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。

*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

### <a name="remarks"></a>備註

這個方法會移除訊息處理常式，對應至所指定的命令識別碼的一群*cmdIDMin*並*cmdIDMax*、 命令來源物件中。

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

移除的命令來源物件中的一群使用者介面的命令訊息處理常式。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>參數

*cmdIDMin*<br/>
命令 ID 範圍的開頭索引。

*cmdIDMax*<br/>
命令 ID 範圍的結束索引。

### <a name="remarks"></a>備註

這個方法會移除使用者介面命令訊息處理常式，對應至所指定的命令識別碼的一群*cmdIDMin*並*cmdIDMax*，命令來源物件中。

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

命令來源物件中移除的使用者介面命令訊息處理常式。

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID。

### <a name="remarks"></a>備註

這個方法會移除的使用者介面命令訊息處理常式對應至*cmdID*命令來源物件中。

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

傳送訊息，並等候它傳回之前進行處理。

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>參數

*command*<br/>
要傳送之訊息的命令識別碼。

### <a name="remarks"></a>備註

這個方法以同步方式傳送的訊息對應到所指定的識別碼*命令*。 它會呼叫[CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)來將訊息放在視窗的訊息佇列並等候，直到該視窗程序已傳回之前處理訊息。

##  <a name="icommandtarget_interface"></a>  ICommandTarget Interface

提供介面，以接收來自命令來源物件的命令中的使用者控制項。

```
interface class ICommandTarget
```

### <a name="remarks"></a>備註

當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 訊息至使用者控制項讓它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。 藉由實作`ICommandTarget`，讓使用者控制物件的參考。

請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`ICommandTarget`。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="initialize"></a>  ICommandTarget::Initialize

初始化命令目標物件。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>參數

*cmdSource*<br/>
命令來源物件的控制代碼。

### <a name="remarks"></a>備註

當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 訊息至使用者控制項讓它處理 MFC 命令。

這個方法會初始化命令目標物件，並將它與指定的命令來源物件相關聯*cmdSource*。 使用者控制項類別實作中，應該呼叫它。 在初始化時，您應該向命令處理常式的命令來源物件呼叫[ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md)在`Initialize`實作。 請參閱[如何：將命令路由新增至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`Initialize`若要這樣做。

##  <a name="icommandui_interface"></a>  ICommandUI 介面

管理使用者介面的命令。

```
interface class ICommandUI
```

### <a name="remarks"></a>備註

這個介面會提供方法和屬性來管理使用者介面的命令。 `ICommandUI` 類似於[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)，差異在於`ICommandUI`用於與.NET 元件交互操作的 MFC 應用程式。

`ICommandUI` 用於`ON_UPDATE_COMMAND_UI`處理常式-衍生的類別中。 功能表中，每個功能表項目時 （選取或按下滑鼠），就會啟動應用程式的使用者會顯示為已啟用或停用。 每個功能表命令的目標是提供這項資訊藉由實作`ON_UPDATE_COMMAND_UI`處理常式。 針對每個命令使用者介面物件，在您的應用程式中，使用 [屬性] 視窗來建立訊息對應項目和每個處理常式的函式原型。

如需有關如何`ICommandUI`介面會在命令路由，請參閱[How to:將命令路由傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

如需有關使用者介面的命令在 MFC 中的管理方式的詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

##  <a name="check"></a>  ICommandUI::Check

此命令的使用者介面項目設為適當的核取狀態。

```
property UICheckState Check;
```

### <a name="remarks"></a>備註

這個屬性會設定為適當的核取狀態的使用者介面項目，此命令。 設定`Check`為下列值：

|詞彙|定義|
|----------|----------------|
|0|取消核取|
|1|檢查|
|2|設定不定|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

會告知命令路由機制繼續路由處理常式鏈結中向下目前的訊息。

```
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是進階的成員函式，應該用於搭配[ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex)處理常式，會傳回 FALSE。 如需詳細資訊，請參閱 < 技術提示[TN006:訊息對應](../../mfc/tn006-message-maps.md)。

##  <a name="enabled"></a>  ICommandUI::Enabled

啟用或停用此命令的使用者介面項目。

```
property bool Enabled;
```

### <a name="remarks"></a>備註

這個屬性會啟用或停用此命令的使用者介面項目。 設定`Enabled`設為 TRUE，在啟用項目，FALSE 來停用它。

##  <a name="id"></a>  ICommandUI::ID

取得所表示之使用者介面物件的識別碼`ICommandUI`物件。

```
property unsigned int ID;
```

### <a name="remarks"></a>備註

這個屬性會取得功能表項目，工具列按鈕的識別碼 （控制代碼），或其他使用者介面物件所表示`ICommandUI`物件。

##  <a name="index"></a>  ICommandUI::Index

取得所表示之使用者介面物件的索引`ICommandUI`物件。

```
property unsigned int Index;
```

### <a name="remarks"></a>備註

這個屬性會取得索引 （控制代碼） 的功能表項目、 工具列按鈕或其他使用者介面物件所表示`ICommandUI`物件。

##  <a name="radio"></a>  ICommandUI::Radio

此命令的使用者介面項目設為適當的核取狀態。

```
property bool Radio;
```

### <a name="remarks"></a>備註

這個屬性會設定為適當的核取狀態的使用者介面項目，此命令。 設定`Radio`設為 TRUE，啟用項目，否則為 FALSE。

##  <a name="text"></a>  ICommandUI::Text

設定的使用者介面項目，此命令的文字。

```
property String^ Text;
```

### <a name="remarks"></a>備註

這個屬性設定的使用者介面項目，此命令的文字。 設定`Text`到文字字串控點。

##  <a name="iview_interface"></a>  IView 介面

會實作數個方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)使用將檢視通知傳送至受管理的控制項。

```
interface class IView
```

### <a name="remarks"></a>備註

`IView` 會實作數個方法，`CWinFormsView`使用轉送至裝載 managed 控制項的一般檢視通知。 這些是[OnInitialUpdate](../../mfc/reference/iview-interface.md)， [OnUpdate](../../mfc/reference/iview-interface.md)並[OnActivateView](../../mfc/reference/iview-interface.md)。

`IView` 類似於[CView](../../mfc/reference/cview-class.md)，但僅適用於受管理的檢視和控制。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="onactivateview"></a>  IView::OnActivateView

啟用或停用檢視時，由 MFC 呼叫。

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>參數

*activate*<br/>
表示正在檢視是否啟用或停用。

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

檢視第一次附加至文件之後，但一開始顯示檢視之前，由架構呼叫。

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

修改檢視的文件之後，由 MFC 呼叫。

```
void OnUpdate();
```

### <a name="remarks"></a>備註

此函式可讓更新以反映修改其顯示的檢視。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
