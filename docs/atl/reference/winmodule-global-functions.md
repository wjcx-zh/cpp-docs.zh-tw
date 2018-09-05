---
title: WinModule 全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08cfa128ecb598d4960c0d5527e66a9cb81266c2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752439"
---
# <a name="winmodule-global-functions"></a>WinModule 全域函式

這些函式提供的支援`_AtlCreateWndData`結構作業。

> [!IMPORTANT]
> 下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

此函式是用來初始化及加入 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>參數

*pWinModule*  
模組的指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。

*pData*  
指標[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)會初始化並新增至目前模組的結構。

*pObject*  
物件的指標**這**指標。

### <a name="remarks"></a>備註

初始化`_AtlCreateWndData`結構，也就用來儲存**這**指標用來參考類別執行個體，並將它加入至模組參考之清單`_ATL_WIN_MODULE70`結構。 由呼叫[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>參數

*pWinModule*  
模組的指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。

### <a name="return-value"></a>傳回值

將指標傳回至[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構。

### <a name="remarks"></a>備註

此函式會擷取現有`_AtlCreateWndData`從清單中的模組所參考的結構`_ATL_WIN_MODULE70`結構。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
