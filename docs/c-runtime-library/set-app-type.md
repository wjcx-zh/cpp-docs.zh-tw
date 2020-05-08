---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 2b78b7205b1e5dda7ac7062747c6dd1065ed1c94
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919921"
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
指出應用程式類型的值。 可能的值包括：

|值|描述|
|----------------|-----------------|
|_crt_unknown_app|不明應用程式類型。|
|_crt_console_app|主控台 (命令列) 應用程式。|
|_crt_gui_app|GUI (Windows) 應用程式。|

## <a name="remarks"></a>備註

您通常不需要呼叫此函式。 它是應用程式呼叫 `main` 之前即執行的 C 執行階段啟始程式碼的一部分。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_set_app_type|process.h|
