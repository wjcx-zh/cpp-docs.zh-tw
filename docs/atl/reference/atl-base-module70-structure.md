---
title: _ATL_BASE_MODULE70 結構
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168640"
---
# <a name="_atl_base_module70-structure"></a>_ATL_BASE_MODULE70 結構

由任何使用 ATL 的專案所使用。

## <a name="syntax"></a>語法

```cpp
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

`cbSize`<br/>
結構的大小，用於版本控制。

`m_hInst`<br/>
此`hInstance`模組的（exe 或 dll）。

`m_hInstResource`<br/>
預設實例資源控制碼。

`m_bNT5orWin98`<br/>
作業系統版本資訊。 由 ATL 在內部使用。

`dwAtlBuildVer`<br/>
儲存 ATL 的版本。 目前0x0700。

`pguidVer`<br/>
ATL 的內部 GUID。

`m_csResource`<br/>
用來同步處理對陣列`m_rgResourceInstance`的存取。 由 ATL 在內部使用。

`m_rgResourceInstance`<br/>
陣列，用來搜尋 ATL 感知的所有資源實例中的資源。 由 ATL 在內部使用。

## <a name="remarks"></a>備註

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定義為 _ATL_BASE_MODULE70 的 typedef。

## <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
