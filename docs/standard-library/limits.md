---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 1527672bd51682bf32c82601ff54a94ea4154a0b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841905"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義類別樣板 `numeric_limits` ，以及兩個有關浮點表示和四捨五入的列舉。

## <a name="requirements"></a>規格需求

**標頭：**\<limits>

**命名空間：** std

## <a name="remarks"></a>備註

類別的明確特製化 `numeric_limits` 描述了許多基本類型的屬性，包括字元、整數和浮點數類型，以及已 **`bool`** 定義的實作為定義，而不是 c + + 語言的規則所修正。 中描述的屬性 \<limits> 包括精確度、最小和最大大小的標記法、舍入和信號類型錯誤。

## <a name="members"></a>成員

### <a name="enumerations"></a>列舉

|名稱|描述|
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[numeric_limits 類別](../standard-library/numeric-limits-class.md)|類別範本描述內建數數值型別的算術屬性。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
