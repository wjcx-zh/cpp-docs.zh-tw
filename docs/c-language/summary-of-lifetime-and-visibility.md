---
title: 存留期和可視性的摘要
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: 5bb53db4d6bcb9b4694fddd9abd5471c6c6197c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474798"
---
# <a name="summary-of-lifetime-and-visibility"></a>存留期和可視性的摘要

下表是多數識別項的存留期和可視性的特性摘要。 前三欄註明定義存留期和可視性的屬性。 若識別項帶有前三欄指定的屬性，其存留期和可視性就如第四和第五欄所示。 不過，此表只包含部分可能的情況。 如需詳細資訊，請參閱[儲存類別](../c-language/c-storage-classes.md)。

### <a name="summary-of-lifetime-and-visibility"></a>存留期和可視性的摘要

|屬性：<br /><br /> 層級|項目|儲存類別<br /><br /> 指定名稱|結果：<br /><br /> 存留期|可視性|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|檔案範圍|變數定義|**static**|Global|發生之原始程式檔的其餘部分|
||變數宣告|**extern**|Global|發生之原始程式檔的其餘部分|
||函式原型或定義|**static**|Global|單一原始程式檔|
||函式原型|**extern**|Global|原始程式檔的其餘部分。|
|區塊範圍|變數宣告|**extern**|Global|區塊|
||變數定義|**static**|Global|區塊|
||變數定義|**auto** 或 **register**|本機|區塊|

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例說明變數的區塊、巢狀和可視性：

### <a name="code"></a>程式碼

```
// Lifetime_and_Visibility.c

#include <stdio.h>

int i = 1;  // i defined at external level

int main()  // main function defined at external level
{
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)
    {                                 // Begin first nested block
        int i = 2, j = 3;          // i and j defined at internal level
        printf_s( "%d %d\n", i, j );  // Prints 2, 3
        {                             // Begin second nested block
            int i = 0;                // i is redefined
            printf_s( "%d %d\n", i, j ); // Prints 0, 3
        }                             // End of second nested block
        printf_s( "%d\n", i );        // Prints 2 (outer definition
                                      //  restored)
    }                                 // End of first nested block
    printf_s( "%d\n", i );            // Prints 1 (external level
                                      // definition restored)
    return 0;
}
```

### <a name="comments"></a>註解

在此範例中，可視性共有四個層級：外部層級和三個區塊層級。 值會列印至螢幕，如每個陳述式之後的註解所示。

## <a name="see-also"></a>請參閱

[存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)