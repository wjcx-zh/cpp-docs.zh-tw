---
title: 物件狀態宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: dc50825d6b6e74dc263a097e86d8ea0d42989825
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495312"
---
# <a name="object-status-macros"></a>物件狀態宏

這個宏會設定屬於 ActiveX 控制項的旗標。

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|用於 ATL ActiveX 控制項中, 以設定 OLEMISC 旗標。|

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

用於 ATL ActiveX 控制項中, 以設定 OLEMISC 旗標。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>參數

*miscstatus*<br/>
所有適用的 OLEMISC 旗標。

### <a name="remarks"></a>備註

這個宏是用來設定 ActiveX 控制項的 OLEMISC 旗標。 如需詳細資訊, 請參閱[IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
