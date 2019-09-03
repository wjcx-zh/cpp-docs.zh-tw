---
title: high_property_prefixes 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219011"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes 匯入屬性

**C++特殊**

為三個屬性方法指定替代的前置詞。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***high_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>參數

*GetPrefix*\
要用於`propget`方法的前置詞。

*PutPrefix*\
要用於`propput`方法的前置詞。

*PutRefPrefix*\
要用於`propputref`方法的前置詞。

## <a name="remarks"></a>備註

根據預設, 高階錯誤處理`propget`、 `propput`和`propputref`方法`Get`會分別以前置詞、 `Put`和`PutRef`命名的成員函式公開。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
