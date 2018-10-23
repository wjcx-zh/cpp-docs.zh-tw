---
title: inject_statement |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27b35c10e9e1953dc45dee1caf61d2e58c38d02d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808639"
---
# <a name="injectstatement"></a>inject_statement

**C + + 特定**

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

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)