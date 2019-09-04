---
title: no_implementation 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220777"
---
# <a name="no_implementation-import-attribute"></a>no_implementation 匯入屬性

**C++特殊**

抑制產生`.tli`標頭, 其中包含包裝函式成員函式的實作為。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_implementation**

## <a name="remarks"></a>備註

如果指定了這個屬性, `.tlh`就會產生標頭 (具有公開類型程式庫專案的宣告), `#include`而不需要包含`.tli`標頭檔的語句。

這個屬性會與[implementation_only](../preprocessor/implementation-only.md)搭配使用。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
