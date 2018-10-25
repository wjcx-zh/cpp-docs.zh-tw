---
title: ICommandTarget 介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee8a4bb3f80d9776aec4fd7a6af0d1523c60064d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066080"
---
# <a name="icommandtarget-interface"></a>ICommandTarget 介面

提供介面，以接收來自命令來源物件的命令中的使用者控制項。

## <a name="syntax"></a>語法

```
interface class ICommandTarget
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|初始化命令目標物件。|

## <a name="remarks"></a>備註

當您裝載在 MFC 檢視中，使用者控制項時[CWinFormsView](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 訊息至使用者控制項讓它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。 藉由實作`ICommandTarget`，讓使用者控制項的參考[ICommandSource](../../mfc/reference/icommandsource-interface.md)物件。

請參閱[如何： 新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用的範例`ICommandTarget`。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）

##  <a name="initialize"></a> ICommandTarget::Initialize

初始化命令目標物件。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>參數

*cmdSource*<br/>
命令來源物件的控制代碼。

### <a name="remarks"></a>備註

當您裝載在 MFC 檢視的使用者控制項時，CWinFormsView 會將命令和更新命令 UI 訊息路由至使用者控制項，以允許它處理 MFC 命令。

這個方法會初始化命令目標物件，並將它與指定的命令來源物件 cmdSource 產生關聯。 使用者控制項類別實作中，應該呼叫它。 在初始化時，您應該在初始化實作中呼叫 ICommandSource::AddCommandHandler 命令來源物件與註冊命令處理常式。 請參閱 < 如何： 將命令路由新增至 Windows Forms 控制項，如需如何執行這項操作時，用以初始化的範例。

## <a name="see-also"></a>另請參閱

[如何：新增命令傳送至 Windows Forms 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource 介面](../../mfc/reference/icommandsource-interface.md)

