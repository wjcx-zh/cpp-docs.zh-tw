---
title: rename_namespace 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216649"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace 匯入屬性

**C++特殊**

將包含類型程式庫內容的命名空間重新命名。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***rename_namespace (** "*NewName*" **)**

### <a name="parameters"></a>參數

*NewName*\
命名空間的新名稱。

## <a name="remarks"></a>備註

**Rename_namespace**屬性會採用單一引數*NewName*, 以指定命名空間的新名稱。

若要移除命名空間, 請改用[no_namespace](../preprocessor/no-namespace.md)屬性。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
