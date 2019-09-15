---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: c4b0caadf20d6c5494acf47ee5a788b5ee009c47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957332"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

[dynamic_cast](../cpp/dynamic-cast-operator.md) 運算子的執行階段實作。

## <a name="syntax"></a>語法

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>參數

*inptr*<br/>
多形物件的指標。

*VfDelta*<br/>
物件中的虛擬函式指標位移。

*SrcType*<br/>
`inptr` 參數指向的物件靜態類型。

*TargetType*<br/>
轉換的預計結果。

*isReference*<br/>
如果輸入是參考，則為 **true**如果輸入是指標，則為 **false**。

## <a name="return-value"></a>傳回值

如果成功，則為適當子物件的指標，否則為 **NULL**。

## <a name="exceptions"></a>例外狀況

如果 `dynamic_cast<>` 的輸入是參考且轉換失敗，則為 `bad_cast()`。

## <a name="remarks"></a>備註

將 `inptr` 轉換為 `TargetType` 類型的物件。 如果 `TargetType` 是指標，則 `inptr` 類型必須是指標；或如果 `TargetType` 是參考，則為左值 (l-value)。 `TargetType` 必須是先前定義的類別類型的指標或參考，或是為 void 的指標。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|