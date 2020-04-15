---
title: 視窗訊息巨集
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329416"
---
# <a name="windows-messages-macros"></a>視窗訊息巨集

此巨集轉發視窗消息。

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|用於將視窗收到的消息轉發到另一個窗口進行處理。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

此宏將視窗接收到的消息轉發到另一個窗口進行處理。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>傳回值

如果處理消息,則非零,如果不是,則為零。

### <a name="remarks"></a>備註

使用WM_FORWARDMSG將視窗收到的消息轉發到另一個窗口進行處理。 LPARAM 和 WPARAM 參數的使用如下:

|參數|使用量|
|---------------|-----------|
|WPARAM|使用者定義的資料|
|LPARAM|指向包含訊息資訊`MSG`的結構的指標|

### <a name="example"></a>範例

在下面的範例中,`m_hWndOther`表示接收此消息的其他視窗。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
