---
title: ICommandTarget 介面
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: be64f4e0367b9ecc1b24fa96f067f4acd45a9978
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751448"
---
# <a name="icommandtarget-interface"></a>ICommandTarget 介面

為使用者提供具有從命令源物件接收命令的介面。

## <a name="syntax"></a>語法

```
interface class ICommandTarget
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICommand 目標::初始化](#initialize)|初始化命令目標物件。|

## <a name="remarks"></a>備註

當您在 MFC 檢視中託管使用者控件時[,CWinFormsView](../../mfc/reference/cwinformsview-class.md)會將命令和命令 UI 訊息更新到使用者控制項,以允許它處理 MFC 命令(例如,架構功能表和工具列按鈕)。 通過實現`ICommandTarget`,向使用者控制件提供對[ICommandSource](../../mfc/reference/icommandsource-interface.md)物件的引用。

有關如何使用,請參閱[:將指令路由新增到 Windows 窗體控制 。](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)`ICommandTarget`

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>需求

**標題**:afxwinforms.h(在程式集 atlmfc_lib_mfcmc80.dll 中定義)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommand 目標::初始化

初始化命令目標物件。

```cpp
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>參數

*cmd 來源*<br/>
命令源物件的句柄。

### <a name="remarks"></a>備註

當您在 MFC 檢視中託管使用者控件時,CWinFormsView 會將命令和命令 UI 消息更新到使用者控制項以允許它處理 MFC 命令。

此方法初始化命令目標物件並將其與指定的命令源物件 cmdSource 關聯。 應在使用者控件類實現中調用它。 在初始化時,應通過在初始化實現中調用 ICommandSource::addCommandHandler,將命令處理程式與命令源物件註冊。 有關如何將命令路由添加到 Windows 窗體控制項,請參閱如何使用初始化執行此操作的範例。

## <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource 介面](../../mfc/reference/icommandsource-interface.md)
