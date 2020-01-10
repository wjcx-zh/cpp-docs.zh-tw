---
title: no_auto_exclude 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216086"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude 匯入屬性

**C++特殊**

停用自動排除。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_auto_exclude**

## <a name="remarks"></a>備註

類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。 它會針對每個要排除的專案發出[編譯器警告 (層級 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) 。 您可以使用這個屬性來停用自動排除。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
