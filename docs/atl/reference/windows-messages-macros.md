---
title: Windows 訊息巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58c9f26b33c3ab2bcdc4e7f0c0a676835da0e3c3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758839"
---
# <a name="windows-messages-macros"></a>Windows 訊息巨集

這個巨集將視窗訊息轉送。

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|使用轉送至另一個視窗中進行處理的視窗所接收的訊息。|  

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

這個巨集將轉送到另一個視窗中進行處理的視窗所接收的訊息。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>傳回值

非零值已處理訊息，如果零如果不是。

### <a name="remarks"></a>備註

您可以使用 WM_FORWARDMSG 轉送到另一個視窗中進行處理的視窗所接收的訊息。 LPARAM 和 WPARAM 參數使用，如下所示：

|參數|使用量|
|---------------|-----------|
|WPARAM|由使用者定義的資料|
|LPARAM|指標`MSG`結構，其中包含訊息的相關資訊|

### <a name="example"></a>範例

在下列範例中，`m_hWndOther`代表接收此訊息的視窗。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
