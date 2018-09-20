---
title: ICommandUI 介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec76a554068dbec050078a0e0558cecd583410c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429199"
---
# <a name="icommandui-interface"></a>ICommandUI 介面

管理使用者介面的命令。

## <a name="syntax"></a>語法

```
interface class ICommandUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[icommandui__Check](#check)|此命令的使用者介面項目設為適當的核取狀態。|
|[ICommandUI::ContinueRouting](#continuerouting)|會告知命令路由機制繼續路由處理常式鏈結中向下目前的訊息。|
|[ICommandUI::Enabled](#enabled)|啟用或停用此命令的使用者介面項目。|
|[ICommandUI::ID](#id)|取得所表示之使用者介面物件的識別碼`ICommandUI`物件。|
|[ICommandUI::Index](#index)|取得所表示之使用者介面物件的索引`ICommandUI`物件。|
|[ICommandUI::Radio](#radio)|此命令的使用者介面項目設為適當的核取狀態。|
|[ICommandUI::Text](#text)|設定的使用者介面項目，此命令的文字。|

## <a name="remarks"></a>備註

這個介面會提供方法和屬性來管理使用者介面的命令。 `ICommandUI` 類似於[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)，差異在於`ICommandUI`用於與.NET 元件交互操作的 MFC 應用程式。

`ICommandUI` 中的 ON_UPDATE_COMMAND_UI 處理常式內使用，且[ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-衍生的類別。 功能表中，每個功能表項目時 （選取或按下滑鼠），就會啟動應用程式的使用者會顯示為已啟用或停用。 每個功能表命令的目標會提供這項資訊藉由實作 ON_UPDATE_COMMAND_UI 處理常式。 針對每個命令使用者介面物件，在您的應用程式中，使用 [屬性] 視窗來建立訊息對應項目和每個處理常式的函式原型。

如需有關如何`ICommandUI`介面會在命令路由，請參閱 <<c2> [ 如何： 新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

如需有關使用者介面的命令在 MFC 中的管理方式的詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。

## <a name="check"></a> ICommandUI::Check

此命令的使用者介面項目設為適當的核取狀態。
```
property UICheckState Check;
```
## <a name="remarks"></a>備註

這個屬性會設定為適當的核取狀態的使用者介面項目，此命令。 將核取設定為下列值：
- 0 取消核取
- 1 檢查
- 設定不定的 2

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

會告知命令路由機制繼續路由處理常式鏈結中向下目前的訊息。
```
void ContinueRouting();
```
## <a name="remarks"></a>備註

這是進階的成員函式，應該會傳回 FALSE 的 ON_COMMAND_EX 處理常式搭配使用。 如需詳細資訊，請參閱技術附註 TN006： 訊息對應。

## <a name="enabled"></a> ICommandUI::Enabled

啟用或停用此命令的使用者介面項目。
```
property bool Enabled;
```
## <a name="remarks"></a>備註

這個屬性會啟用或停用此命令的使用者介面項目。 將啟用 設定為 true 啟用項目，為 FALSE，則將它停用。

## <a name="id"></a> ICommandUI::ID

取得 ICommandUI 物件所表示的使用者介面物件的識別碼。
```
property unsigned int ID;
```
## <a name="remarks"></a>備註

這個屬性會取得功能表項目、 工具列按鈕或其他使用者介面物件 ICommandUI 物件所代表的識別碼 （控制代碼）。

## <a name="index"></a> ICommandUI::Index

取得 ICommandUI 物件所表示的使用者介面物件的索引。
```
property unsigned int Index;
```
## <a name="remarks"></a>備註

這個屬性會取得功能表項目、 工具列按鈕或其他使用者介面物件 ICommandUI 物件所表示的索引 （控制代碼）。

## <a name="radio"></a> ICommandUI::Radio

此命令的使用者介面項目設為適當的核取狀態。
```
property bool Radio;
```
## <a name="remarks"></a>備註

這個屬性會設定為適當的核取狀態的使用者介面項目，此命令。 設定選項，以 true 以啟用項目;否則為 FALSE。

## <a name="text"></a> ICommandUI::Text

設定的使用者介面項目，此命令的文字。
```
property String^ Text;
```
## <a name="remarks"></a>備註

這個屬性設定的使用者介面項目，此命令的文字。 設定文字的文字字串控制代碼。

## <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)
