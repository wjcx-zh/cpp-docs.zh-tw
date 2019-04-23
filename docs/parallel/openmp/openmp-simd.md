---
title: SIMD 擴充功能
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60125170"
---
# <a name="simd-extension"></a>SIMD 擴充功能

視覺化C++目前支援 OpenMP 2.0 標準，但 Visual Studio 2019 現在也提供 SIMD 功能。

> [!NOTE]
> 若要使用 SIMD，以編譯`-openmp:experimental`使用時，可讓無法使用的其他 OpenMP 功能的交換器`-openmp`切換。
>
> `-openmp:experimental`交換器 visitor `-openmp`，這表示所有的 OpenMP 2.0 功能都包含在其使用。

如需詳細資訊，請參閱 < [SIMD 擴充功能C++Visual Studio 中的 OpenMP](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)。

## <a name="openmp-simd-in-visual-c"></a>視覺效果中的 OpenMP SIMDC++

OpenMP SIMD，導入在 OpenMP 4.0 標準，使向量友善迴圈的目標。 使用`simd`迴圈之前指示詞，編譯器可以忽略向量相依性，讓迴圈為向量便於越好，並採用使用者打算有多個迴圈反覆項目同時執行。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

視覺化C++提供類似的非 OpenMP 迴圈 pragma 喜歡`#pragma vector`並`#pragma ivdep`，但使用 OpenMP SIMD 編譯器可以執行的詳細資訊，例如：

- 一律允許忽略出現的向量相依性。
- `/fp:fast` 在迴圈內啟用。
- 外部迴圈和函式呼叫的迴圈是向量友善。
- 巢狀的迴圈可以聯合成一個迴圈，並進行向量友善。
- 混合式加速`#pragma omp for simd`來啟用廣泛的多執行緒處理和更細緻的向量。  

向量友善迴圈，編譯器仍無訊息，除非您使用向量支援 log 參數：

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

非向量易記迴圈，則編譯器會發出每個訊息：

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>子句

OpenMP SIMD 指示詞也可增強向量支援下列子句：

|指示詞|描述|
|---|---|
|`simdlen(length)`|指定向量的行的數。|
|`safelen(length)`|指定的向量相依性的距離。|
|`linear(list[ : linear-step]`)|迴圈歸納變數從陣列的訂用帳戶的線性對應。|
|`aligned(list[ : alignment])`|資料的對齊方式。|
|`private(list)`|指定資料 「 私有化 」。|
|`lastprivate(list)`|指定資料私有化最終的值，從最後一個反覆項目。|
|`reduction(reduction-identifier:list)`|指定自訂的縮減作業。|
|`collapse(n)`|聯合迴圈巢狀結構。|

> [!NOTE]
> 非有效 SIMD 子句不會剖析與警告與編譯器忽略。
>
> 例如，使用下列程式碼問題的警告：
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>範例
  
OpenMP SIMD 指示詞可用來指示編譯器進行迴圈向量友善的使用者。 加上附註與 OpenMP SIMD 指示詞的迴圈，使用者會想要擁有多個迴圈反覆項目同時執行。

例如，下列迴圈 OpenMP SIMD 指示詞附註。 因為沒有回溯相依性 [i] [i-1]，但因為 SIMD 指示詞，編譯器仍可以封裝到一個向量指令的第一個陳述式的連續的反覆項目，並執行會在迴圈反覆項目之間沒有完美的平行處理原則它們以平行方式。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

因此，下列已轉換的向量形式的迴圈是**法律**因為編譯器會保留每個原始的迴圈反覆項目的循序的行為。 亦即`a[i]`之後執行`a[-1]`，`b[i]`之後`a[i]`的呼叫與`bar`上次發生。

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

它有**不合法**移動記憶體參考`*c`跳出迴圈，如果它與別名可能`a[i]`或`b[i]`。 也是不重新排列一個原始的反覆項目內的陳述式，一旦違反了循序的相依性。 例如，下列的轉換的迴圈不合法的：

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>另請參閱

[/openmp (啟用 OpenMP 2.0 支援)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
