---
title: auto_inline |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083174"
---
# <a name="autoinline"></a>auto_inline
排除的範圍中定義的任何函式所在**關閉**指定其視為自動內嵌展開的候選項目。

## <a name="syntax"></a>語法

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>備註

若要使用**auto_inline** pragma，將它放之前和之後 （不在） 函式定義。 pragma 會在顯示該 pragma 後的第一個函式定義生效。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)