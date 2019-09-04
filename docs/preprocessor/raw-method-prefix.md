---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216139"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++特殊**

指定不同的前置詞，避免發生名稱衝突。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>參數

*前置詞*\
要使用的前置詞。

## <a name="remarks"></a>備註

低層級的屬性和方法是由使用預設前置詞**raw_** 的成員函式所公開, 以避免與高階錯誤處理成員函式發生名稱衝突。

> [!NOTE]
> [Raw_interfaces_only](raw-interfaces-only.md)屬性存在時, **raw_method_prefix**屬性的效果不會變更。 **Raw_method_prefix**一律`raw_interfaces_only`優先于指定前置詞。 如果同時在相同`#import`的語句中使用這兩個屬性, 則會使用**raw_method_prefix**屬性所指定的前置詞。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
