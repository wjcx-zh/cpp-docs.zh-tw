---
title: no_namespace 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220733"
---
# <a name="no_namespace-import-attribute"></a>no_namespace 匯入屬性

**C++特殊**

指定編譯器不會產生命名空間名稱。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_namespace**

## <a name="remarks"></a>備註

`#import` 標頭檔中的類型程式庫內容通常是在命名空間中定義。 命名空間名稱是在原始 IDL `library`檔案的語句中指定。 如果已指定**no_namespace**屬性, 則此命名空間不會由編譯器產生。

如果您想要使用不同的命名空間名稱, 請改用[rename_namespace](../preprocessor/rename-namespace.md)屬性。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
