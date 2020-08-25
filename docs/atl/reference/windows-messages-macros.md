---
title: Windows 訊息宏
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: b4cd3c2eea24449eb17050b147d9c59560d8358f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834436"
---
# <a name="windows-messages-macros"></a>Windows 訊息宏

這個宏會轉送視窗訊息。

|名稱|描述|
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|用來將視窗接收的訊息轉送到另一個視窗進行處理。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a> WM_FORWARDMSG

此宏會將視窗接收的訊息轉送到另一個視窗進行處理。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>傳回值

如果已處理訊息，則為非零，否則為零。

### <a name="remarks"></a>備註

使用 WM_FORWARDMSG 將視窗接收的訊息轉送到另一個視窗進行處理。 LPARAM 和 WPARAM 參數的使用方式如下：

|參數|使用方式|
|---------------|-----------|
|WPARAM|由使用者定義的資料|
|LPARAM|`MSG`結構的指標，其中包含訊息的相關資訊|

### <a name="example"></a>範例

在下列範例中， `m_hWndOther` 表示接收此訊息的另一個視窗。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
