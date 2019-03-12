---
title: _set_app_type
ms.date: 11/04/2016
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 5a29fd94cca7fdbf6bbb24699b7f510bf1465f15
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749187"
---
# <a name="setapptype"></a>_set_app_type

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

|值|說明|
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
