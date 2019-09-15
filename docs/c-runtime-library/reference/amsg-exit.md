---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 2d577bfcf0584ef982ab43ff98674d0cfadd14ba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939702"
---
# <a name="_amsg_exit"></a>_amsg_exit

發出指定的執行階段錯誤訊息，然後以錯誤碼 255 結束應用程式。

## <a name="syntax"></a>語法

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>參數

*rterrnum*<br/>
系統定義之執行階段錯誤訊息的識別碼。

## <a name="remarks"></a>備註

此函式會向主控台應用程式的 **stderr** 發出執行階段錯誤訊息，或在 Windows 應用程式的訊息方塊中顯示訊息。 在偵錯模式中，您可以選擇在結束之前叫用偵錯工具。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_amsg_exit|internal.h|