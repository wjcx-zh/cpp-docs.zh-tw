---
title: inject_statement
ms.date: 10/18/2018
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 237ca796028aad7aff55442eb2806fe400330a29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383720"
---
# <a name="injectstatement"></a>inject_statement

**C++特定**

將其做為來源文字的引數插入至類型程式庫標題。

## <a name="syntax"></a>語法

```
inject_statement("source_text")
```

### <a name="parameters"></a>參數

*source_text*<br/>
要插入至類型程式庫標題檔案的來源文字。

## <a name="remarks"></a>備註

文字會放置在命名空間宣告的開頭位置，該命名空間宣告會在標題檔案中包裝類型程式庫內容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)