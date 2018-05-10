---
title: '#行指示詞 （C/c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 10/18/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#line'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ebbcea7432b27e9269b5041d90d14534a77b812
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="line-directive-cc"></a>#line 指示詞 (C/C++)

`#line` 指示詞指示前置處理器，將編譯器內部儲存的行號和檔名變更為特定行號和檔名。

## <a name="syntax"></a>語法

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>備註

編譯器會使用這個行號和選擇性檔名來指向它在編譯期間發現的錯誤。 行號通常參考目前的輸入行，檔名則參考目前的輸入檔。 每次一行程式碼處理後，行號會遞增。

*數字順序*值可以是任何整數常數。 在前置處理語彙基元上可以執行巨集取代，不過結果必須評估為正確的語法。 *Filename*可以是任何字元的組合和必須括在雙引號內 (**""**)。 如果*filename*已省略，則為前一個檔名維持不變。

您可以撰寫 `#line` 指示詞，修改原始程式碼行號和檔名。 轉譯器使用的行號和檔名來決定值的預先定義的巨集 **&#95;&#95;檔案&#95;&#95;** 和 **&#95;&#95;列&#95;&#95;**. 您可以使用這些巨集，將自述性的錯誤訊息插入程式文字中。 如需有關這些預先定義的巨集的詳細資訊，請參閱[預先定義巨集](../preprocessor/predefined-macros.md)。

**&#95;&#95;檔案&#95;&#95;** 巨集會展開為字串，其內容是檔名，以雙引號括住 (**""**)。

如果您變更行號和檔名，編譯器會忽略先前的值並以新的值繼續處理。 程式產生器通常使用 `#line` 指示詞產生錯誤訊息，以參考原始程式檔，而非產生的程式。

下列範例說明`#line`和 **&#95;&#95;列&#95;&#95;** 和 **&#95;&#95;檔案&#95;&#95;** 巨集。

在此陳述式，在內部儲存的行號被設為 151，檔名變更為 copy.c。

```cpp
#line 151 "copy.c"
```

 在此範例中，巨集`ASSERT`使用預先定義的巨集 **&#95;&#95;列&#95;&#95;** 和 **&#95;&#95;檔案&#95;&#95;** 列印如果給定的判斷提示不是 true 來源檔案的相關錯誤訊息。

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)