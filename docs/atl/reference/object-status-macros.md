---
title: 物件狀態宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326170"
---
# <a name="object-status-macros"></a>物件狀態宏

此宏設置屬於 ActiveX 控制件的標誌。

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|用於 ATL ActiveX 控制件,用於設置 OLEMISC 標誌。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

用於 ATL ActiveX 控制件,用於設置 OLEMISC 標誌。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>參數

*錯誤狀態*<br/>
所有適用的 OLEMISC 標誌。

### <a name="remarks"></a>備註

此宏用於為 ActiveX 控件設置 OLEMISC 標誌。 有關詳細資訊,請參閱[IOleObject:獲取 MiscCStatus。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
