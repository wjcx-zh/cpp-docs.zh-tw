---
title: push_macro |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6a389289f8849ac6155543299392586dcd389d2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078943"
---
# <a name="pushmacro"></a>push_macro
儲存的值*macro_name*這個巨集的堆疊頂端的巨集。

## <a name="syntax"></a>語法

```
#pragma push_macro("
macro_name
")
```

## <a name="remarks"></a>備註

您可以擷取的值*macro_name*使用`pop_macro`。

請參閱[pop_macro](../preprocessor/pop-macro.md)如需相關範例。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)