---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389316"
---
# <a name="exclude-import"></a>排除 (\#匯入)

**C++特定**

排除從類型程式庫標頭檔產生的項目。

## <a name="syntax"></a>語法

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>參數

*Name1*<br/>
要排除的第一個項目。

*Name2*<br/>
要排除的第二個項目 (如果需要的話)。

## <a name="remarks"></a>備註

類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 這個屬性可以接受任意數目的引數，每一個都是要排除的頂層類型程式庫項目。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)