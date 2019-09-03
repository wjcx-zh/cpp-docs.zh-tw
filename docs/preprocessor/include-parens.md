---
title: include () 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 39ab63525b2b83781cbcaf86a61742c5fb767b72
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218874"
---
# <a name="include-import-attribute"></a>include () 匯入屬性

**C++特殊**

停用自動排除。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***include ("** _Name1_ **"** [ __, "__ *Name2* __"__ ...] __)__

### <a name="parameters"></a>參數

*Name1*\
要強制包含的第一個項目。

*Name2*\
要強制包含的第二個項目 (如果需要的話)。

## <a name="remarks"></a>備註

類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。 如果不應自動排除某些專案, 您可能會看到[編譯器警告 (層級 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)。 您可以使用這個屬性來停用自動排除。 這個屬性可以接受任意數目的引數, 每個類型程式庫專案的名稱各包含一個。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
