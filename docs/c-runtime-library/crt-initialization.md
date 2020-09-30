---
title: CRT 初始化
description: 描述 CRT 如何初始化機器碼中的全域狀態。
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 25f1e2a7e5b7d91c729bb45bd79ba9a8720cead1
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589766"
---
# <a name="crt-initialization"></a>CRT 初始化

本主題說明 CRT 如何以機器碼初始化全域狀態。

根據預設，連結器會包含能自行提供起始程式碼的 CRT 程式庫。 此起始程式碼會初始化 CRT 程式庫，呼叫全域初始設定式，然後呼叫由使用者針對主控台應用程式所提供的 `main` 函式。

## <a name="initializing-a-global-object"></a>初始化全域物件

請考慮下列程式碼：

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

根據 C/C++ 標準，`func()` 必須在執行 `main()` 之前呼叫。 但呼叫它的是誰？

判斷呼叫端的其中一種方式，是在中設定中斷點 `func()` 、將應用程式進行偵錯工具，以及檢查堆疊。 之所以可以這麼做，是因為 CRT 原始程式碼包含在 Visual Studio 之中。

當您流覽堆疊上的函式時，您會看到 CRT 正在呼叫函式指標清單。 這些函數類似于 `func()` 或類別實例的函式。

CRT 會從 Microsoft c + + 編譯器取得函式指標清單。 當編譯器看到全域初始化運算式時，它會在區段中產生動態初始化運算式， `.CRT$XCU` 其中 `CRT` 是區段名稱，而 `XCU` 是組名。 若要取得動態初始化運算式的清單，請執行命令 **dumpbin/all main .obj**，然後搜尋 `.CRT$XCU` 區段。 當主要 .cpp 編譯為 c + + 檔案，而不是 C 檔案時，就會套用這項功能。 它會類似下列範例：

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                               Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  -------
00000000  DIR32             00000000           C         ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT 會定義兩個指標：

- `.CRT$XCA` 中的 `__xc_a`

- `.CRT$XCZ` 中的 `__xc_z`

除了和以外，群組都沒有定義任何其他符號 `__xc_a` `__xc_z` 。

現在，當連結器讀取各個 `.CRT` 群組時，它會將它們結合成單一區段，並依字母順序加以排序。 這代表使用者定義的全域初始設定式 (Microsoft C++ 編譯器會將它置於 `.CRT$XCU` 中) 將會一律位於 `.CRT$XCA` 之後，以及 `.CRT$XCZ` 之前。

區段會類似下列範例：

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

因此，CRT 程式庫會使用 `__xc_a` 和 `__xc_z` 來判斷全域初始化運算式清單的開始和結束，因為它們是在載入映射後於記憶體中配置的方式。

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
