---
title: SIMD 延伸模組
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366457"
---
# <a name="simd-extension"></a>SIMD 延伸模組

Visual C++目前支援 OpenMP 2.0 標準,但 Visual Studio 2019 現在還提供 SIMD 功能。

> [!NOTE]
> 要使用 SIMD,請`-openmp:experimental`使用交換機進行編譯,該開關啟用`-openmp`使用 交換機時不可用的其他 OpenMP 功能。
>
> `-openmp:experimental`開關的底入`-openmp`,這意味著所有OpenMP 2.0功能都包含在它的使用中。

有關詳細資訊,請參閱[在可視化工作室中C++ OpenMP 的 SIMD 擴展](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/)。

## <a name="openmp-simd-in-visual-c"></a>視覺C++中的 OPENMP SIMD

OpenMP SIMD,在 OpenMP 4.0 標準中引入,目標是使向量友好環路。 通過使用迴圈前的`simd`指令,編譯器可以忽略向量依賴項,使迴圈盡可能友好向量,並尊重使用者同時執行多個迴圈反覆運算的意圖。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

可視C++提供類似的非 OpenMP 循環雜`#pragma vector`注`#pragma ivdep`, 例如 與,但是使用 OpenMP SIMD,編譯器可以執行更多作業,例如:

- 始終允許忽略當前向量依賴項。
- `/fp:fast`在迴圈中啟用。
- 具有函數調用的外部迴圈和迴圈是向量友好的。
- 嵌套迴圈可以合併到一個迴圈中,使向量友好。
- 混合加速度`#pragma omp for simd`,實現粗粒度多線程和細粒度向量。  

對於向量友好型循環,編譯器將保持靜音狀態,除非您使用向量支援日誌開關:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

對於非向量友好循環,編譯器會為每個迴圈發出一條消息:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>子句

OpenMP SIMD 指令還可以採用以下子句來增強向量支援:

|指示詞|描述|
|---|---|
|`simdlen(length)`|指定向量通道數。|
|`safelen(length)`|指定向量依賴項距離。|
|`linear(list[ : linear-step]`)|從環路感應變數到陣列訂閱的線性映射。|
|`aligned(list[ : alignment])`|數據的對齊方式。|
|`private(list)`|指定數據私有化。|
|`lastprivate(list)`|使用上次反覆運算中的最終值指定數據私有化。|
|`reduction(reduction-identifier:list)`|指定自定義的縮減操作。|
|`collapse(n)`|合併迴圈嵌套。|

> [!NOTE]
> 無效的 SIMD 子句由編譯器使用警告進行解析和忽略。
>
> 例如,使用以下代碼會發出警告:
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
  
OpenMP SIMD 指令為使用者提供了一種指令編譯器使迴圈向量友好的方法。 通過使用 OpenMP SIMD 指令對循環進行加號,使用者打算同時執行多個循環反覆運算。

例如,以下迴圈使用OpenMP SIMD 指令進行帶號表示。 迴圈反覆運算之間沒有完美的並行性,因為從 a_i] 到 {i-1} 存在向後依賴關係,但由於 SIMD 指令,編譯器仍允許將第一個語句的連續反覆運算打包到一個向量指令中並並行運行它們。

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

因此,迴圈的以下轉換向量形式**是合法的**,因為編譯器保留每個原始迴圈反覆運算的順序行為。 換句話`a[i]`說,在之後`a[-1]`執行`b[i]``a[i]`,`bar`調用 後發生最後。

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

`a[i]`如果記憶體參考可能與 或`b[i]`要被合法`*c`的名稱, 則會存到下一個循環**是不合法的**。 如果語句打破了順序依賴項,則在原始反覆運算中重新排序語句也不合法。 例如,以下轉換的循環不合法:

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
