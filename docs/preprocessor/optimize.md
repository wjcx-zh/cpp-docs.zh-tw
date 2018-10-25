---
title: 最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98275f6e0a16c6d07b66ce592eb12b9391157653
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069733"
---
# <a name="optimize"></a>optimize

指定要依照函式逐一執行的最佳化。

## <a name="syntax"></a>語法

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>備註

**最佳化**pragma 必須出現在函式之外，並顯示該 pragma 後定義的第一個函式才會生效。 *上*並*off*引數開啟選項中指定*最佳化清單*開啟或關閉。

*最佳化清單*可以是零個或多個參數下, 表所示。

### <a name="parameters-of-the-optimize-pragma"></a>最佳化 Pragma 的參數

|參數|最佳化類型|
|--------------------|--------------------------|
|*g*|啟用全域最佳化。|
|*s*或*t*|指定機器碼的短 (short) 序列或快速 (fast) 序列。|
|*y*|在程式堆疊上產生框架指標。|

這些是與所用的相同字母[/O](../build/reference/o-options-optimize-code.md)編譯器選項。 例如，下列 pragma 相當於 `/Os` 編譯器選項：

```
#pragma optimize( "ts", on )
```

使用**最佳化**pragma 搭配空字串 (**"」**) 是一種特殊形式的指示詞：

當您使用*關閉*參數，會讓所有的最佳化*g*， *s*， *t*，並*y*、 設為 off。

當您使用*上*參數，會最佳化重設為指定的[/O](../build/reference/o-options-optimize-code.md)編譯器選項。

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)