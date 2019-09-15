---
title: __set_app_type
ms.date: 11/04/2016
api_name:
- __set_app_type
- _set_app_type
api_location:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: 4d72eecd454e6c01e88c6869c96b628902690383
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940231"
---
# <a name="__set_app_type"></a>__set_app_type

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