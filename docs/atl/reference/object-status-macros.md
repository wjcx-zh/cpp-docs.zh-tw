---
title: 物件狀態宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: d9e2223739dc3d0636337e2e2f713c80dff50131
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835229"
---
# <a name="object-status-macros"></a>物件狀態宏

這個宏會設定屬於 ActiveX 控制項的旗標。

|名稱|描述|
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|用於 ATL ActiveX 控制項來設定 OLEMISC 旗標。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a> DECLARE_OLEMISC_STATUS

用於 ATL ActiveX 控制項來設定 OLEMISC 旗標。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>參數

*miscstatus*<br/>
所有適用的 OLEMISC 旗標。

### <a name="remarks"></a>備註

這個宏是用來設定 ActiveX 控制項的 OLEMISC 旗標。 如需詳細資訊，請參閱 [IOleObject：： GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
