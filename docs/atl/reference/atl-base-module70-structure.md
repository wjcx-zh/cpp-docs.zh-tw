---
title: _ATL_BASE_MODULE70 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7218d7fc8886cffdcce13f09a682fdc635f84f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759924"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 結構

使用任何使用 ATL 的專案

## <a name="syntax"></a>語法

```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>成員

`cbSize`  
結構，用來進行版本設定的大小。

`m_hInst`  
`hInstance`此模組 （exe 或 dll）。

`m_hInstResource`  
預設執行個體資源控制代碼。

`m_bNT5orWin98`  
作業系統版本資訊。 供內部使用 ATL

`dwAtlBuildVer`  
儲存 ATL 的版本 目前 0x0700。

`pguidVer`  
ATL 的內部 GUID。

`m_csResource`  
用來同步存取`m_rgResourceInstance`陣列。 供內部使用 ATL

`m_rgResourceInstance`  
用來搜尋資源的 ATL 並知道的所有資源執行個體的陣列。 供內部使用 ATL

## <a name="remarks"></a>備註

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定義為 _ATL_BASE_MODULE70 的 typedef。

## <a name="requirements"></a>需求

**標頭：** atlcore.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)

