---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 6521fe0a5bfbe482bf2aed8f5a32221abdc6d6d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531586"
---
# <a name="renamenamespace"></a>rename_namespace

**C + + 特定**

將包含類型程式庫內容的命名空間重新命名。

## <a name="syntax"></a>語法

```
rename_namespace("NewName")
```

### <a name="parameters"></a>參數

*NewName*<br/>
命名空間的新名稱。

## <a name="remarks"></a>備註

它接受單一引數， *NewName*，以指定的命名空間的新名稱。

若要移除的命名空間，請使用[no_namespace](../preprocessor/no-namespace.md)改為屬性。

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)