---
title: _set_app_type
ms.date: 11/04/2016
api_name:
- _set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 7e04d88d9e9981e35b7d4c80c11d27c868219f65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957917"
---
# <a name="_set_app_type"></a>_set_app_type

在啟動時使用的內部函式會告訴 CRT，應用程式是主控台應用程式或 GUI 應用程式。

## <a name="syntax"></a>語法

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>參數

*appType*<br/>
指出應用程式類型的值。 可能值為：

|值|描述|
|----------------|-----------------|
|_crt_unknown_app|不明應用程式類型。|
|_crt_console_app|主控台 (命令列) 應用程式。|
|_crt_gui_app|GUI (Windows) 應用程式。|

## <a name="remarks"></a>備註

您通常不需要呼叫此函式。 它是應用程式呼叫 `main` 之前即執行的 C 執行階段啟始程式碼的一部分。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_set_app_type|process.h|
