---
title: raw_property_prefixes 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216047"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes 匯入屬性

**C++特殊**

為三個屬性方法指定替代的前置詞。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***raw_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>參數

*GetPrefix*\
要`propget`用於方法的前置詞。

*PutPrefix*\
要`propput`用於方法的前置詞。

*PutRefPrefix*\
要`propputref`用於方法的前置詞。

## <a name="remarks"></a>備註

根據預設, 低層級`propget`的`propput`、和`propputref`方法會由名為的成員函式 ( `get_`分別`put_`使用、 `putref_`和的前置詞) 公開。 這些前置詞與標頭檔中使用由 MIDL 所產生的名稱相容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
