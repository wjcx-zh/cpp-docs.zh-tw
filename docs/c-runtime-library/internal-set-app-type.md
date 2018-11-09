---
title: __set_app_type
ms.date: 11/04/2016
apiname:
- __set_app_type
- _set_app_type
apilocation:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: f42ac1c173637cf85d727adf25ebf9079f4cb37c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457482"
---
# <a name="setapptype"></a>__set_app_type

設定目前的應用程式類型。

## <a name="syntax"></a>語法

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>參數

*at*<br/>
指出應用程式類型的值。 可能值為：

|值|描述|
|-----------|-----------------|
|_UNKNOWN_APP|不明應用程式類型。|
|_CONSOLE_APP|主控台 (命令列) 應用程式。|
|_GUI_APP|GUI (Windows) 應用程式。|

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__set_app_type|internal.h|